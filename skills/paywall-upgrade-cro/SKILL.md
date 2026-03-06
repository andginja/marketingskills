---
name: paywall-upgrade-cro
description: |
  Optimize in-app upgrade prompts, paywall screens, and free-to-paid conversion flows. Activate with phrases like:
  "optimize paywall", "improve upgrade conversion", "paywall design review",
  "increase free to paid conversion", "upgrade prompt optimization",
  "trial expiration flow", "feature gating strategy", "pricing modal review",
  "plan comparison optimization", "upsell flow", "monetization optimization"
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - cro
    - paywall
    - upgrade
    - monetization
    - saas
    - pricing
---

# Paywall and In-App Upgrade CRO

You are an expert in free-to-paid conversion and in-app upgrade optimization. When given a paywall screen, upgrade prompt, or monetization strategy, you evaluate the gating logic, prompt design, timing, and messaging to maximize upgrade rate without damaging user experience or long-term retention.

## Core Principle: Value Before Gate

```
Upgrade Motivation = Experienced Value + Anticipated Value - Perceived Cost - Switching Risk
```

Users upgrade when they have already experienced enough value to trust the product AND can clearly see that paying unlocks meaningfully more value. Every paywall interaction must reinforce both.

## Feature Gating Strategy

### Gating Models

| Model | How It Works | Best For | Risk |
|---|---|---|---|
| **Feature-limited** | Free plan has fewer features; paid unlocks advanced ones | Products with clear basic vs power-user split | Free plan must still be useful — too limited kills activation |
| **Usage-limited** | Free plan has a cap (messages, projects, storage) | Products where value scales with usage | Cap must be generous enough for aha moment but tight enough to hit |
| **Time-limited (trial)** | Full access for N days, then paywall | Products where core value requires full access to experience | Must deliver aha moment before trial ends or conversion craters |
| **Seat-limited** | Free for 1 user, paid for teams | Collaboration tools | Solo user must see team value before hitting the gate |
| **Capacity-limited** | Free tier processes up to X, paid handles more | API tools, processing platforms | Set the threshold where real workloads begin |
| **Support-limited** | Free = community/docs only, paid = direct support | All products (as a secondary gate) | Weak standalone gate — pair with feature or usage limits |

### Gating Decision Framework

For each feature, answer:

1. **Is this feature needed to reach the aha moment?** If yes, include it in free. Gating it kills activation.
2. **Does this feature's value increase with scale/usage?** If yes, usage-gate it (free up to N, paid beyond).
3. **Is this feature primarily valuable to power users or teams?** If yes, feature-gate it in a higher plan.
4. **Does this feature create ongoing operational cost?** If yes, it is a candidate for paid tier.

### The Aha-Then-Gate Rule

Never place a gate before the user has experienced the core value of your product. The correct sequence is:

```
Signup -> Experience value (aha moment) -> Hit the gate -> Upgrade
```

Not:

```
Signup -> Hit the gate -> ??? -> User never experiences value -> Churn
```

If your free-to-paid conversion rate is below 2%, your gate is likely placed before the aha moment.

### Free Tier Benchmarks

| Metric | Poor | Average | Good | Excellent |
|---|---|---|---|---|
| Free-to-paid conversion (overall) | <1% | 2-4% | 5-7% | 8-12% |
| Free-to-paid conversion (activated users) | <5% | 8-12% | 15-25% | 25%+ |
| Trial-to-paid conversion | <15% | 20-30% | 35-50% | 50%+ |
| Time to upgrade (from signup) | >90 days | 30-60 days | 14-30 days | <14 days |

## Upgrade Prompt Design

### The Upgrade Prompt Framework

Every upgrade prompt needs four elements:

1. **Context**: Why is the user seeing this right now? (They hit a limit, used a gated feature, etc.)
2. **Value**: What specifically will they get by upgrading?
3. **Proof**: Why should they trust that upgrading is worth it?
4. **Action**: A clear, low-friction path to upgrade.

### Upgrade Prompt Types

| Type | Trigger | Design | Example |
|---|---|---|---|
| **Soft nudge** | User approaches a limit | Banner or inline callout, dismissible | "You've used 8 of 10 free projects. Upgrade for unlimited." |
| **Hard gate** | User attempts a paid feature | Modal or inline blocker | "Export to PDF is available on the Pro plan. Upgrade to unlock." |
| **Usage milestone** | User hits a usage threshold | Celebratory modal or banner | "You've sent 500 emails this month — you're outgrowing the free plan." |
| **Feature discovery** | User hovers over or clicks a locked feature | Tooltip or inline expansion | Lock icon + "Pro feature — see what's included" |
| **Contextual upsell** | User is in a workflow where a paid feature would help | Subtle inline suggestion | "Tip: With Pro, you can automate this step" |
| **Trial expiration** | Trial period is ending | Email + in-app banner + modal | "Your trial ends in 2 days — keep everything you've built" |

### Upgrade Prompt Copy

#### Headline Formulas

| Formula | Example |
|---|---|
| Unlock [feature] to [outcome] | "Unlock advanced analytics to see what's really driving growth" |
| You've outgrown [plan] — time for [plan] | "You've outgrown Free — upgrade to Pro for unlimited projects" |
| Keep [what they've built/done] | "Keep your 47 automations running — upgrade before your trial ends" |
| [Number] teams use [plan] to [outcome] | "12,000 teams use Pro to ship 3x faster" |
| Ready for [next level outcome]? | "Ready to automate your entire workflow?" |

#### Body Copy Rules

1. **Lead with what they gain, not what they lack**: "Get unlimited projects" not "You've hit your project limit"
2. **Be specific about what's included**: Bullet 3-5 key features they will unlock
3. **Quantify the value**: "Save 5 hours per week with automated reports"
4. **Acknowledge their investment**: "You've already built 12 projects — keep the momentum going"
5. **Reduce risk**: "Cancel anytime", "30-day money-back guarantee", "No long-term contract"

#### CTA Button Copy

| Weak | Strong |
|---|---|
| Upgrade | Upgrade to Pro — $29/mo |
| Buy now | Start my Pro trial |
| Subscribe | Unlock unlimited projects |
| See plans | Compare plans and pricing |

**Rule**: Always show the price or "free trial" in or near the CTA. Hidden pricing creates anxiety and distrust.

### Dismiss / Decline Options

Always provide a clear way to dismiss upgrade prompts. Options:

| Dismiss Copy | Tone |
|---|---|
| "Maybe later" | Neutral, non-committal |
| "Continue with Free plan" | Clear and respectful |
| "Remind me next week" | Defers but keeps the door open |
| "I'm not ready yet" | Empathetic |

Never guilt-trip or hide the dismiss option. Aggressive upgrade prompts destroy goodwill and accelerate churn.

## Usage-Based Triggers

### When to Show Upgrade Prompts

| Trigger Point | Why It Works | Prompt Type |
|---|---|---|
| **75% of limit** | Warning before frustration | Soft nudge (banner) |
| **90% of limit** | Urgency is real, action is imminent | Prominent banner |
| **100% of limit (hard stop)** | User cannot proceed without upgrading | Modal with clear value prop |
| **100% of limit (soft stop)** | User can continue but with degraded experience | Inline message + upgrade CTA |
| **After completing key action** | User is in a success moment, high motivation | Celebratory upsell |
| **After N sessions** | User is engaged enough to evaluate paid | In-app banner or settings prompt |
| **Feature attempt** | User clicked a paid feature for the first time | Contextual tooltip or modal |

### Trigger Frequency Rules

| Rule | Setting | Rationale |
|---|---|---|
| Same upgrade prompt | Max once per session | Repeating creates annoyance |
| After dismissal | Wait 3-7 days before re-showing | Respect the user's timing |
| Across all upgrade surfaces | Max 2 upgrade touchpoints per session | Dashboard banner + one contextual prompt |
| After explicit "not interested" | Suppress for 30+ days | User has made a deliberate choice |

## Plan Comparison Design

### Comparison Table Best Practices

1. **Highlight the recommended plan** with a visual indicator (border, badge, background color)
2. **Use checkmarks, not feature descriptions** in the comparison grid — save descriptions for tooltips
3. **Lead with the features that matter most** to the target audience, not an exhaustive list
4. **Group features by category**: Core, Collaboration, Analytics, Support, etc.
5. **Show price per user/month** as the primary number, with annual savings secondary
6. **Include a row for usage limits** (projects, seats, storage) — this is often the real differentiator
7. **Add a "Most Popular" badge** to the plan you want most users on
8. **Limit to 3-4 plans** visible at once — more creates decision paralysis

### Comparison Table Layout

```
|               | Free        | Pro            | Business       |
|---------------|-------------|----------------|----------------|
| Price         | $0          | $29/user/mo    | $79/user/mo    |
| Projects      | 10          | Unlimited      | Unlimited      |
| Storage       | 1 GB        | 50 GB          | 500 GB         |
| Team members  | 1           | 10             | Unlimited      |
| Analytics     | Basic       | Advanced       | Custom reports |
| Support       | Community   | Email (24h)    | Priority (1h)  |
| SSO/SAML      | -           | -              | Checkmark      |
| API access    | -           | Checkmark      | Checkmark      |
|               | [Current]   | [Upgrade]*     | [Contact sales]|
```

*Highlight column with visual emphasis.

### Plan Name Strategy

Plan names should signal the target customer, not arbitrary size:

| Avoid | Use Instead | Why |
|---|---|---|
| Bronze / Silver / Gold | Starter / Professional / Enterprise | Signals who the plan is for |
| Tier 1 / Tier 2 / Tier 3 | Solo / Team / Organization | Describes the user, not a hierarchy |
| Basic / Standard / Premium | Free / Pro / Business | "Basic" implies inadequacy |

## Social Proof in Upgrade Flows

### Where to Place Social Proof

| Location | Proof Type | Example |
|---|---|---|
| Upgrade modal | Customer quote about ROI | "Upgrading to Pro saved our team 10 hours/week" — Sarah, VP Ops |
| Plan comparison page | Logo bar of companies on each plan | [Logos] "Trusted by 5,000 Pro teams" |
| Trial expiration email | Specific outcome stat | "Pro users see 3x more pipeline than Free users" |
| Feature gate tooltip | Usage stat | "47% of users who unlock this feature see results in the first week" |
| Payment page | Trust badges + guarantee | "30-day money-back guarantee. Cancel anytime." |

### Social Proof Copy for Upgrade Context

| Type | Template |
|---|---|
| Outcome-based | "[Company] increased [metric] by [X%] after upgrading to [Plan]" |
| Peer pressure | "[N] teams upgraded to [Plan] this month" |
| Expert endorsement | "Rated #1 in [category] by [Authority]" |
| Risk reduction | "Join [N] teams. 30-day money-back guarantee." |
| FOMO (use sparingly) | "[N] users on your plan have already upgraded" |

## Trial Expiration Handling

### The Trial Expiration Sequence

| Days Before Expiration | Channel | Message Focus |
|---|---|---|
| **7 days** | Email | Value recap: "Here's what you've accomplished so far" |
| **3 days** | Email + in-app banner | Feature preview: "These Pro features will be locked in 3 days" |
| **1 day** | Email + in-app modal | Urgency + loss aversion: "Tomorrow, you'll lose access to [features]" |
| **Expiration day** | Email + full-screen modal on login | Clear choice: upgrade, downgrade, or extend |
| **1 day after** | Email | Win-back: "We saved your data — upgrade anytime to pick up where you left off" |
| **3 days after** | Email | Last attempt: Different angle (offer, discount, or call) |
| **7 days after** | Email | Final: "Your [Product] data will be archived in 7 days" |

### Trial Expiration Page Design

The expiration page (shown when the user logs in after trial ends) should include:

1. **What they will lose** (specific features and data, not generic "premium access")
2. **What they have built** ("You created 12 projects, invited 4 teammates, and sent 230 messages")
3. **Plan options** with the recommended plan pre-selected
4. **Downgrade option** clearly visible (do not hide it — trust increases conversion)
5. **Extension option** if applicable ("Need more time? Get 7 more days free")
6. **Support contact** for users with questions

### Loss Aversion Messaging

Frame the expiration in terms of what the user will lose, not what they will gain:

| Gain Framing (Weaker) | Loss Framing (Stronger) |
|---|---|
| "Upgrade to keep using advanced analytics" | "You'll lose access to your custom dashboards and reports" |
| "Get unlimited projects with Pro" | "Your 15 projects will be locked — only 3 accessible on Free" |
| "Continue collaborating with your team" | "Your 4 teammates will lose access tomorrow" |

Loss aversion is 2-2.5x more motivating than equivalent gains (Kahneman & Tversky). Use it ethically — be factual, not manipulative.

## Discount and Offer Strategy

### When to Offer Discounts

| Scenario | Offer Type | Discount Level |
|---|---|---|
| Trial expired, no action after 3 days | Time-limited discount | 20-30% off first 3 months |
| User on free plan for 60+ days, active | Annual plan incentive | 20% off annual (vs monthly) |
| User downgraded from paid | Win-back offer | 30-50% off for 1-2 months |
| Competitor comparison page visitor | Match or beat | Case-by-case |
| Enterprise prospect in negotiation | Custom pricing | Volume discount |

### Discount Cautions

- Never offer discounts in the first upgrade prompt — train users to wait for deals
- Always frame discounts as time-limited and reason-specific
- Discounts on annual plans are safer than monthly (longer commitment, higher LTV)
- Track discount-driven cohorts separately — do they retain as well as full-price customers?

## Paywall Screen Audit Output Format

When auditing a paywall or upgrade flow, deliver:

### 1. Gating Assessment
Is the gate placed after the aha moment? Is the free tier generous enough for activation but constrained enough to drive upgrades?

### 2. Prompt Design Review
Evaluate copy, design, timing, and frequency of all upgrade touchpoints.

### 3. Plan Comparison Review
Assess clarity, visual hierarchy, recommended plan emphasis, and pricing presentation.

### 4. Trial Expiration Flow Review
Evaluate the email and in-app sequence around trial end.

### 5. Quick Wins
Copy changes, prompt timing adjustments, social proof additions.

### 6. Strategic Recommendations
Gating model changes, new trigger points, offer strategy.

### 7. Metrics to Track
Conversion funnel by trigger, plan distribution, discount cohort retention.

## Related Skills
- [onboarding-cro](../onboarding-cro/SKILL.md) — Ensure users are activated before they hit the paywall
- [page-cro](../page-cro/SKILL.md) — Optimize the public pricing page
- [ab-test-setup](../ab-test-setup/SKILL.md) — Test paywall variations and pricing experiments
- [signup-flow-cro](../signup-flow-cro/SKILL.md) — Optimize the path to trial signup
