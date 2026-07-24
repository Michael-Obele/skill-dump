# Principles Deep Dive — Conversion Psychology

This reference file contains extended breakdowns, code examples, and edge cases for each of the six UX psychology principles. Load this only when the user asks for deeper detail or when you need expanded implementation guidance.

---

## 1. Smart Defaults

### Edge Cases
- **Privacy-sensitive defaults:** Never pre-fill sensitive data (passwords, payment details) without explicit user consent. Use device-stored values with user opt-in.
- **Geo-detection fallbacks:** If geo-detection fails (VPN, unknown locale), fall back to the most widely compatible default rather than showing an error.
- **Power users:** Provide a way to clear all defaults with one click — "Start fresh" link next to pre-filled forms.

### Code Pattern: Context-Aware Defaults

```typescript
type FormDefaults = {
  country: string
  currency: string
  language: string
  plan: 'monthly' | 'annual'
  seats: number
}

function detectDefaults(): FormDefaults {
  const locale = typeof navigator !== 'undefined'
    ? navigator.language || 'en-US'
    : 'en-US'

  const detectedCountry = guessCountryFromLocale(locale) // via geo headers or locale

  return {
    country: detectedCountry,
    currency: getCurrencyForCountry(detectedCountry),
    language: locale,
    plan: 'annual', // higher value, pre-selected as "savings"
    seats: 1,       // most common starting point
  }
}
```

### CTA Copy Transformation

| Before | After |
|--------|-------|
| "Submit" | "Search 12 Available Options" |
| "Sign Up" | "Create My Workspace" |
| "Get Started" | "Start My Free Audit" |
| "Buy Now" | "Unlock Team Access" |
| "Learn More" | "See My Personalized Plan" |

---

## 2. Goal Gradient Effect

### Edge Cases
- **Short flows (< 3 steps):** Don't show a progress bar — it highlights how little there is. Use subtle step indicators instead.
- **Recovery flows:** If a user returns to a partially completed flow, restore their progress from storage. Never reset to 0%.
- **Abandoned flows:** Store progress in localStorage so returning users resume where they left off, preserving the momentum.

### Progress Calculation Formula

```typescript
function initializeProgress(totalSteps: number): { currentStep: number; percent: number } {
  // Never start at 0%. Count initialization as completion of step 0 (conceptually).
  const artificialStart = Math.round((1 / totalSteps) * 100)
  return {
    currentStep: 1,
    percent: Math.max(artificialStart, 20), // minimum 20%
  }
}
```

### Animation Pattern

```css
.progress-bar {
  transition: width 400ms cubic-bezier(0.34, 1.56, 0.64, 1);
  /* Overshoot easing — feels rewarding */
}

.step-complete {
  animation: pop 300ms cubic-bezier(0.34, 1.56, 0.64, 1);
}

@keyframes pop {
  0% { transform: scale(1); }
  50% { transform: scale(1.2); }
  100% { transform: scale(1); }
}
```

---

## 3. Reciprocity

### Edge Cases
- **Preview vs paywall balance:** Show enough value to demonstrate utility, but not so much that the user has no reason to convert. 60% preview, 40% locked is a common split.
- **Time-limited reciprocity:** Free trials with immediate value. 7-day full access beats 30-day limited access in conversion studies.
- **No-data previews:** If you need user data to generate value, use anonymized sample data for the preview, then swap in real data post-auth.

### Reciprocity Pattern: Progressive Disclosure

```typescript
interface PreviewState {
  revealed: boolean    // has the user seen the preview?
  unlocked: boolean   // has the user authenticated?
  previewData: any    // anonymized or partial data
}

// Step 1: Show preview without auth (reciprocity)
// Step 2: User experiences value
// Step 3: Gate the "full report" behind lightweight auth
// Step 4: Reveal complete data with user's actual information
```

### Real-World Data
- Notion's conversion flow: Full product access before subscription → 2x higher activation rate than gated onboarding
- Grammarly: Free browser extension builds habit before premium upsell → 4% free-to-paid conversion

---

## 4. IKEA Effect & Endowment

### Edge Cases
- **Too much customization:** Limit pre-auth configuration to 3-4 choices. Analysis paralysis kills the effect.
- **Transient users:** Save customizations in localStorage with a session identifier so returning users (even pre-auth) recover their choices.
- **Low-stakes products:** The IKEA Effect is strongest when the customization is meaningful. For simple tools, use theme/color selection or naming.

### State Persistence Pattern

```typescript
const PRE_AUTH_KEY = 'conversion-psychology:workspace-draft'

interface WorkspaceDraft {
  name: string
  theme: 'light' | 'dark' | 'system'
  role: string
  industry: string
  goals: string[]
  createdAt: number
}

function saveDraft(draft: WorkspaceDraft): void {
  localStorage.setItem(PRE_AUTH_KEY, JSON.stringify({
    ...draft,
    createdAt: Date.now(),
  }))
}

function recoverDraft(): WorkspaceDraft | null {
  const raw = localStorage.getItem(PRE_AUTH_KEY)
  if (!raw) return null
  return JSON.parse(raw) as WorkspaceDraft
}
```

### CTA Language Shift

| Before | After | Why |
|--------|-------|-----|
| "Sign Up" | "Save My Workspace" | Ownership framing |
| "Create Account" | "Continue with My Settings" | Progress framing |
| "Register" | "Lock In My Preferences" | Investment framing |

---

## 5. Loss Aversion

### Edge Cases
- **Overuse fatigue:** If every modal uses loss framing, users become desensitized. Reserve for high-value conversion points (upgrade, cancel, delete).
- **Negative brand perception:** Aggressive loss framing can feel manipulative. Pair with value-positive messaging to balance.
- **Data-less users:** If the user has no data at risk (new visitor), loss framing doesn't work. Fall back to Gain Framing or Reciprocity.

### Dismissal Copy Decision Tree

```
User clicks "X" on upgrade modal:
├── User has active data (drafts, projects, files)
│   └── "I'll risk losing my [drafts/projects/files]"
├── User has consumed content (viewed, read)
│   └── "I'll lose access to my content"
└── User is new (no data, no history)
    └── "Maybe later" (gain framing — loss doesn't apply)
```

### Urgency Signal Pattern

```typescript
function getUrgencyProps(userItems: { name: string; count: number }) {
  if (userItems.count === 0) {
    return {
      primaryCta: "Start Free Trial",
      dismissText: "Not right now",
      framing: "gain", // no loss to leverage
    }
  }

  return {
    primaryCta: `Keep My ${userItems.count} ${userItems.name}`,
    dismissText: `I'll risk losing my ${userItems.name}`,
    framing: "loss",
    detailLine: `${userItems.name.slice(0, 2).join(", ")}${userItems.count > 2 ? ` and ${userItems.count - 2} more` : ""}`,
  }
}
```

---

## 6. Contrast Effect

### Edge Cases
- **Too extreme anchoring:** If the anchor price is absurdly high, it undermines trust. Enterprise tier should be 3-5x the target, not 100x.
- **No anchor available:** When there's no higher tier or competitor price to reference, use the "cost of doing nothing" or manual alternative.
- **Mobile constraints:** On small screens, anchor pricing can dominate. Use collapsible comparison sections or horizontal scroll.

### Pricing Anchor Calculation

```typescript
interface PricingTier {
  name: string
  price: number
  isAnchor?: boolean
  isTarget?: boolean
  isAddOn?: boolean
}

function computeContrastContext(
  target: PricingTier,
  anchor: PricingTier,
): { savingsLabel: string; relativePercent: string } {
  const savings = anchor.price - target.price
  const annualSavings = savings * 12
  const percentOfAnchor = ((target.price / anchor.price) * 100).toFixed(1)

  return {
    savingsLabel: `Save $${annualSavings}/year`,
    relativePercent: `${percentOfAnchor}% of ${anchor.name}`,
  }
}

function computeAddOnContext(
  addOnPrice: number,
  mainItemPrice: number,
): string {
  const percent = ((addOnPrice / mainItemPrice) * 100).toFixed(1)
  return `+${percent}% of your order`
}
```

### Common Contrast Patterns

| Pattern | Example | Effect |
|---------|---------|--------|
| Good-Better-Best | Basic $10 / Pro $29 / Enterprise $99 | Pro feels like the sweet spot |
| Decoy pricing | Print $15 / Digital $10 / Bundle $15 | Bundle dominates (decoy makes it obvious) |
| Penny gap | Monthly $10 / Annual $100 ($8.33/mo) | Annual feels like a clear savings |
| Cost of inaction | "Manual processing costs you $5,000/yr" | Our $500/yr tool feels trivial |

---

## Combining Principles

The highest-converting designs combine multiple principles at once. Here are proven combinations:

### Onboarding Flow (Goal Gradient + IKEA Effect + Smart Defaults)
1. User arrives → auto-detect geo/language [Smart Defaults]
2. "Step 1 of 4: Your Goal" — already 25% complete [Goal Gradient]
3. User picks theme, name, role → saved to localStorage [IKEA Effect]
4. Live preview renders as they customize [IKEA Effect + Reciprocity]
5. Final step: "Save My Workspace" — email/password [Reciprocity]

### Upgrade Modal (Loss Aversion + Contrast Effect + IKEA Effect)
1. Modal opens with user's draft count visible [Loss Aversion]
2. Current plan limitations shown next to upgrade benefits [Contrast Effect]
3. "Keep your projects" vs "I'll lose access" [Loss Aversion + IKEA Effect]
4. Annual pre-toggled with savings badge [Smart Defaults + Contrast Effect]

### Checkout Flow (Contrast Effect + Goal Gradient + Smart Defaults)
1. Progress bar starts at "Cart review" — 33% [Goal Gradient]
2. Original prices crossed out, savings highlighted [Contrast Effect]
3. Add-ons shown with "+X% of order" badges [Contrast Effect]
4. Default shipping method pre-selected [Smart Defaults]
5. "Free returns" guarantee near CTA [Loss Aversion]
