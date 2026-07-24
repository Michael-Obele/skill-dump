# Page-Type Playbook — Conversion Psychology

Component-specific implementation guides with before/after patterns for each major page type.

---

## Landing Pages

### Hero Section

**Before (generic):**
```
+------------------------------------------+
|  Hero Image                              |
|                                          |
|  [Headline: "Welcome to Our Product"]    |
|  [Subheadline: "We help teams..."]       |
|                                          |
|  [Get Started] [Learn More]              |
+------------------------------------------+
```

**After (conversion-optimized):**
```
+------------------------------------------+
|  [Free ROI Calculator / Audit Tool]       |  ← Reciprocity
|  Estimate your team's savings             |  ← IKEA Effect (interactive)
|  [Industry ▼] [Team Size ▼]              |
|  [Calculate My Savings →]                |
|                                          |
|  "Teams like yours waste $12K/yr         |  ← Loss Aversion
|   on manual processes"                   |
|                                          |
|  [See My Free Audit]  ●  No credit card  |  ← Smart Defaults CTA
+------------------------------------------+
```

### Lead Capture Section

**Before:**
```
+------------------------------------------+
|  Sign up for our newsletter              |
|                                          |
|  Name: [___________]                     |
|  Email: [___________]                    |
|  Company: [___________]                  |
|  Role: [___________]                     |
|  Phone: [___________]                    |
|                                          |
|  [Submit]                                |
+------------------------------------------+
```

**After:**
```
+------------------------------------------+
|  Get Your Free Industry Report           |  ← Reciprocity
|                                          |
|  Step 1 of 3 ████░░░░░░░ 40%            |  ← Goal Gradient
|                                          |
|  What industry are you in?               |
|  [Technology ▼]                          |  ← Smart Defaults
|                                          |
|  [Continue →]                            |
+------------------------------------------+
```

---

## Pricing Tables

### Before (flat list):
```
+-------+-------+--------+---------------+
| Basic | Pro   | Enterprise              |
| $10   | $29   | $99                     |
| [Buy]  | [Buy]  | [Contact]              |
+-------+-------+--------+---------------+
```

### After (psychology-optimized):
```
+---------+----------+---------------+------------------+
| Basic   | Pro      | Enterprise    | Cost of Doing    |
| $10/mo  | $29/mo   | $99/mo        | Nothing           |
|         | ★ MOST   |               | $5,000/yr        |
|         | POPULAR  |               | (your current     |
|         |          |               |  manual process)  |
| [Start]  | [Start]  | [Contact]    |                   |
| Free     | Free     |              |                   |
|         | ▸ Save   |              |                   |
|         |   $228/yr |              |                   |  ← Contrast Effect
+---------+----------+---------------+------------------+
           ↑                                             ↑
    Smart Defaults                              Contrast Anchor
    (pre-toggled annual,
    "Most Popular" badge)
```

### Feature Comparison (Loss Aversion)

When comparing tiers, frame lower tiers by what they're *missing*:

| Feature | Free | Pro |
|---------|------|-----|
| Projects | 3 | Unlimited ✗ you lose access after 3 |
| Storage | 10MB | 10GB ✗ your files won't fit |
| Team | 1 seat | 10 seats ✗ your team can't collaborate |
| Export | — | CSV, PDF, API ✗ you can't export your data |

---

## Onboarding & Signup Flows

### Before (wall of fields):
```
+------------------------------------------+
|  Create Your Account                     |
|                                          |
|  Full Name: [________________]           |
|  Email: [________________]               |
|  Password: [________________]            |
|  Company: [________________]             |
|  Role: [________________]                |
|  Team Size: [________________]           |
|  How did you hear: [________________]    |
|                                          |
|  [Sign Up]                               |
+------------------------------------------+
```

### After (progressive disclosure with psychology):

**Step 1 — IKEA Effect + Goal Gradient (20% complete)**
```
+------------------------------------------+
|  ██░░░░░░░░  20%                         |  ← Goal Gradient
|                                          |
|  Let's set up your workspace             |
|                                          |
|  Workspace name: [My Team's Projects ▼]  |  ← Smart Defaults
|  Industry: [Technology ▼]                |
|  Role: [Developer ▼]                     |
|                                          |
|  [Continue →]                            |
+------------------------------------------+
```

**Step 2 — IKEA Effect + Reciprocity**
```
+------------------------------------------+
|  ████░░░░░░  40%                         |
|                                          |
|  Pick your theme (preview updates live)  |
|                                          |
|  [🌙 Dark] [☀️ Light] [🌿 System]        |
|                                          |
|  [Preview of workspace with theme]       |  ← Live preview
|                                          |
|  [Continue →]                            |
+------------------------------------------+
```

**Step 3 — Reciprocity (value before gate)**
```
+------------------------------------------+
|  ██████░░░░  60%                         |
|                                          |
|  Here's what we found for you            |
|                                          |
|  [Dashboard preview with sample data]    |  ← Preview value
|  - 12 optimization opportunities found   |
|  - Estimated 34% improvement             |
|                                          |  ← Reciprocity
|  [Unlock My Full Report]                 |
+------------------------------------------+
```

**Step 4 — Auth (now they're invested)**
```
+------------------------------------------+
|  ██████████  80%                         |
|                                          |
|  Save your workspace — one more step     |
|                                          |
|  Email: [user@example.com ▼]             |  ← Smart Defaults
|  Password: [••••••••••]                  |
|                                          |
|  [Save My Workspace]                     |  ← IKEA Effect copy
|                                          |
|  "Your 3 preferences are saved."         |  ← Loss Aversion (they'd lose it)
+------------------------------------------+
```

---

## Login Flows

### Before:
```
+------------------------------------------+
|  Welcome Back                            |
|                                          |
|  Email: [________________]               |
|  Password: [________________]            |
|                                          |
|  [Log In]    [Forgot Password?]          |
+------------------------------------------+
```

### After:
```
+------------------------------------------+
|  Welcome back, you have 3 notifications  |  ← Reciprocity (value preview)
|                                          |
|  Continue as [user@example.com]          |  ← Smart Defaults
|  [Not you? Log in with another account]  |
|                                          |
|  ──── or ────                           |
|                                          |
|  [● Continue with Google]               |  ← Contrast Effect
|  [○ Continue with GitHub]  │  [Other]   |  (SSO visually dominant)
|                                          |
|  [Password]                          [→] |
|                                          |
|  "Don't lose your progress —             |  ← Loss Aversion
|   sign in to sync your data"             |
+------------------------------------------+
```

---

## Upgrade Modals

### Before:
```
+------------------------------------------+
|  Upgrade to Pro                          |
|                                          |
|  Get unlimited projects, team access,    |
|  and priority support.                   |
|                                          |
|  [$29/mo]                                |
|                                          |
|  [No thanks]    [Upgrade Now]            |
+------------------------------------------+
```

### After:
```
+------------------------------------------+
|  ⚠  You've used 3 of 5 free projects    |  ← Goal Gradient
|                                          |
|  Keep your active projects:              |
|  • Q3 Dashboard     ← will be archived   |  ← Loss Aversion
|  • Marketing Site   ← will be archived   |  (named items at risk)
|  • API Docs         ← will be archived   |
|                                          |
|  ┌──────────────────────────────┐         |
|  │ Upgrade to Pro — $29/mo     │         |  ← Contrast Effect
|  │ Save $60/yr with annual     │         |  (annual pre-toggled)
|  │ ★ Most Popular              │         |
|  └──────────────────────────────┘         |
|                                          |
|  [Keep My Projects]  [I'll risk losing]  |  ← Loss Aversion dismissals
|  ▲ Primary CTA        ▲ Explicit choice  |
+------------------------------------------+
```

---

## CTAs & Buttons (Micro-Patterns)

### CTA Copy Matrix

| Context | Don't Say | Say Instead | Principle |
|---------|-----------|-------------|-----------|
| Onboarding step | "Next" | "Continue →" | Goal Gradient |
| Onboarding final | "Sign Up" | "Save My Workspace" | IKEA Effect |
| Checkout | "Buy Now" | "Secure My Order" | Loss Aversion |
| Free trial end | "Upgrade" | "Keep My Access" | Loss Aversion |
| Report/result | "Submit" | "Unlock My Results" | Reciprocity |
| Pricing page | "Get Started" | "Start Saving" | Contrast Effect |
| Login | "Log In" | "Continue Where I Left Off" | Goal Gradient |
| Modal dismiss | "No thanks" | "I'll risk losing my data" | Loss Aversion |
| Form submit | "Send" | "See My Personalized Plan" | Smart Defaults |

### Visual Weight Hierarchy

```
+------------------------------------------+
|                                          |
|     [I'll risk losing]                   |  ← Secondary: lighter weight, smaller
|                                          |
|  ┌──────────────────────────────────┐     |
|  │       Keep My 3 Drafts           │     |  ← Primary: full weight, brand color
|  └──────────────────────────────────┘     |
|                                          |
+------------------------------------------+
```

The primary CTA should be visually dominant (brand color, filled, larger). The secondary should be visually subdued (ghost/text style, smaller). This anchoring effect (Contrast Effect) makes the primary feel like the obvious choice.

---

## Empty States

### Before:
```
+------------------------------------------+
|                                          |
|              📭                          |
|     No projects yet                      |
|                                          |
|  [Create Project]                        |
|                                          |
+------------------------------------------+
```

### After:
```
+------------------------------------------+
|                                          |
|              🚀                          |
|  "Your first project is 30 seconds       |  ← Goal Gradient
|   away"                                  |
|                                          |
|  Start with a template:                  |  ← Smart Defaults
|  [E-commerce]  [SaaS]  [Portfolio]       |
|                                          |
|  [Create My First Project →]             |  ← IKEA Effect CTA
|                                          |
+------------------------------------------+
```

---

## Error & Recovery Flows

### Before:
```
+------------------------------------------+
|  ❌ Error                                |
|  Something went wrong. Try again.        |
|                                          |
|  [Try Again]                             |
+------------------------------------------+
```

### After:
```
+------------------------------------------+
|  😅 Our bad                              |  ← Blame the system
|  We couldn't save your workspace.        |  ← Specific, not generic
|  Your draft is still here (we cached it).|  ← Loss Aversion (safety)
|                                          |
|  [Try Again]   [Email me my draft]       |  ← Reciprocity + Recovery
|                                          |
+------------------------------------------+
```
