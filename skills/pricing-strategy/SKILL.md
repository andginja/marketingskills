---
name: pricing-strategy
description: |
  SaaS pricing and monetization strategy. Use when the user asks about:
  - pricing strategy or pricing model
  - SaaS pricing or subscription pricing
  - value-based pricing
  - pricing tiers or packaging
  - pricing page design or optimization
  - price increases or raising prices
  - pricing research or willingness to pay
  - pricing psychology or anchoring
  - freemium vs free trial
  - per-seat vs usage-based pricing
  - Good-Better-Best pricing
  - Van Westendorp or MaxDiff analysis
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - pricing
    - monetization
    - saas
---

# SaaS Pricing Strategy

## The Three Pricing Axes

Every pricing decision involves three independent axes. Most companies obsess over price point and ignore the other two, which often have a larger impact on revenue.

### Axis 1: Packaging (What is included at each tier)
This is the most strategic decision. Packaging determines who buys what and creates natural upgrade paths.

**Key principles:**
- Each tier should target a distinct buyer persona, not just offer "more of the same."
- The jump between tiers should feel justified by a clear capability unlock, not just higher limits.
- Features that drive stickiness (integrations, collaboration, automation) belong in higher tiers.
- Features that drive adoption (core functionality, ease of use) belong in lower tiers.

### Axis 2: Pricing Metric (What you charge per unit of)
The pricing metric is the unit that scales with the customer's usage or success. Choosing the right metric is the highest-leverage pricing decision you can make.

**Criteria for a good pricing metric:**
- **Aligned with value:** The customer pays more as they get more value. Per-seat pricing works when each seat represents a user getting value. Per-API-call works when each call generates business value.
- **Predictable:** Customers should be able to estimate their bill. Unpredictable pricing creates purchase anxiety and churn.
- **Scalable:** The metric should grow as the customer grows, creating natural expansion revenue without requiring a sales conversation.
- **Simple to understand:** If you need a calculator to explain your pricing, the metric is too complex.

### Axis 3: Price Point (The actual dollar amount)
The specific number attached to each tier. This is where most pricing discussions start, but it should come last.

**Price point principles:**
- Price based on value delivered, not cost to serve. Your margins are not the customer's concern.
- Research willingness to pay before setting prices. Do not guess.
- Round numbers signal premium. Precise numbers ($49, $97) signal value or optimization.
- Annual discounts of 15-20% are standard. More than 25% signals desperation.

## Value Metrics Deep Dive

### Per User (Per Seat)
**Best for:** Collaboration tools, CRMs, project management, communication platforms.

**Pros:**
- Simple to understand and predict.
- Revenue scales linearly with organizational adoption.
- Low friction to start (buy one seat, expand later).

**Cons:**
- Creates an incentive to share logins, reducing your revenue and data quality.
- Penalizes the customer for growing their team, which creates friction.
- Does not capture value differences between a power user and a casual user.

**Variations:**
- Per active user (only charge for users who log in) — reduces friction but creates revenue volatility.
- Tiered user pricing (1-5 users at one rate, 6-20 at another) — smooths the expansion curve.
- Per user with role-based pricing (admins at full price, viewers free) — captures value differences.

### Per Usage
**Best for:** Infrastructure, API services, messaging platforms, data processing.

**Pros:**
- Perfectly aligned with value — customers pay only for what they use.
- Low barrier to entry (start small, grow naturally).
- Strong expansion revenue as usage grows.

**Cons:**
- Revenue is unpredictable for both you and the customer.
- Creates anxiety about "the bill" which can suppress usage.
- Requires sophisticated metering and billing infrastructure.

**Mitigation strategies:**
- Offer committed use discounts (commit to X usage/month for a lower rate).
- Provide spending caps or alerts.
- Bundle a base allocation into each tier, with overage pricing above it.

### Per Feature
**Best for:** Horizontal platforms where different customers need different capabilities.

**Pros:**
- Clear upgrade triggers — customers upgrade when they need a specific capability.
- Allows precise targeting of different personas with different tiers.
- Each tier has a distinct value proposition.

**Cons:**
- Gating the wrong feature in the wrong tier destroys conversion.
- Complexity increases as you add features — tier boundaries become arbitrary over time.
- Customers resent paying for features they consider basic.

**Rules for feature gating:**
- Never gate a feature that takes less than 5 minutes to use. The perceived value is too low for an upgrade trigger.
- Gate features that serve power users or specific use cases, not core workflows.
- If more than 40% of users on a tier request a gated feature, it belongs in that tier.

### Flat Fee
**Best for:** Simple products, early-stage startups, or products where usage does not vary much across customers.

**Pros:**
- Maximum simplicity — one price, one offering.
- Easy to communicate and sell.
- Predictable revenue for you and predictable cost for the customer.

**Cons:**
- Leaves money on the table from high-value customers.
- No natural expansion revenue.
- Difficult to serve both small and large customers with a single price.

## Good-Better-Best Tier Framework

The GBB model is the most reliable tier structure for SaaS. Three tiers, each targeting a distinct persona.

### Good (Starter / Basic)
- **Target:** Individual users, small teams, or price-sensitive buyers.
- **Purpose:** Drive adoption and convert free users to paid. This is your gateway.
- **Pricing:** Low enough that it is an impulse decision. Under $20/month for SMB, under $50/month for mid-market.
- **Include:** Core functionality, basic integrations, limited usage. Enough to be genuinely useful.
- **Exclude:** Advanced features, premium support, team collaboration.

### Better (Pro / Growth)
- **Target:** Growing teams and serious users. This is your volume tier.
- **Purpose:** Capture the majority of your revenue. 60-70% of paying customers should land here.
- **Pricing:** 2-3x the Good tier. This is your anchor — most customers will compare Good and Best, then land on Better.
- **Include:** Everything in Good, plus the features that drive team adoption, more usage, and key integrations.
- **Exclude:** Enterprise features (SSO, audit logs, custom contracts, SLAs).

### Best (Business / Enterprise)
- **Target:** Large teams, regulated industries, or customers with complex requirements.
- **Purpose:** Capture high-value customers and maximize revenue per account.
- **Pricing:** 3-5x the Better tier. Or "Contact Us" for true enterprise.
- **Include:** Everything in Better, plus SSO/SAML, advanced permissions, dedicated support, SLAs, custom integrations, admin controls.
- **Why these features here:** SSO, audit logs, and compliance features have near-zero marginal cost but extremely high willingness to pay from enterprise buyers.

### Tier Design Principles
- The Better tier should be visually highlighted as "Most Popular" — this is your anchor.
- Feature lists should be cumulative ("Everything in Pro, plus...") not independent.
- Limit tiers to 3, or at most 4 (adding a free tier). More tiers create decision paralysis.
- Every tier needs at least one "must-have" feature that the tier below lacks.

## Pricing Research Methods

### Van Westendorp Price Sensitivity Meter
Ask four questions to a sample of your target customers (minimum 30 respondents for usable data, 100+ for reliable data):

1. At what price would this be **so cheap** you would question its quality?
2. At what price would this be a **bargain** — a great buy for the money?
3. At what price would this start to get **expensive** but you would still consider it?
4. At what price would this be **too expensive** — you would never consider buying it?

**How to analyze:**
- Plot cumulative frequency distributions for each question.
- The intersection of "too cheap" and "not expensive" gives you the **point of marginal cheapness** (floor).
- The intersection of "not cheap" and "too expensive" gives you the **point of marginal expensiveness** (ceiling).
- The intersection of "too cheap" and "too expensive" gives you the **optimal price point** (OPP).
- The intersection of "cheap" and "expensive" gives you the **indifference price point** (IDP).
- Your acceptable price range is between marginal cheapness and marginal expensiveness.

### MaxDiff Analysis (Best-Worst Scaling)
Used to determine which features matter most to customers, which directly informs packaging.

- Present sets of 4-5 features and ask respondents to pick the "most important" and "least important" in each set.
- Rotate features across multiple sets so every feature appears an equal number of times.
- Calculate a utility score for each feature based on how often it was picked as best vs worst.
- Group features into tiers based on their utility scores: high-utility features go in higher tiers.

**When to use MaxDiff over simple ranking:**
- When you have more than 8 features to evaluate (ranking becomes unreliable above 8).
- When you need statistically defensible prioritization.
- When features are not obviously comparable (apples vs oranges).

### Conjoint Analysis
More sophisticated than Van Westendorp. Presents respondents with product configurations (bundles of features at different prices) and asks them to choose between options. Reveals the marginal value of each feature and the price elasticity of the overall package.

- Use for major pricing overhauls or new product launches.
- Requires larger sample sizes (200+) and statistical expertise.
- Tools like Conjointly, Sawtooth, or SurveyMonkey can simplify implementation.

## When and How to Raise Prices

### Signals That You Should Raise Prices
- Your close rate on proposals is above 80% — you are leaving money on the table.
- Customers frequently say you are "underpriced" or a "great deal."
- Your product has significantly improved since the last pricing change.
- Competitors with similar (or inferior) products charge more.
- Your CAC payback period is longer than 12 months — you need more revenue per customer.
- You have not changed pricing in over 18 months.

### How to Execute a Price Increase
1. **Grandfather existing customers** for 6-12 months. This preserves trust and reduces churn risk.
2. **Communicate the increase 60-90 days in advance** for annual customers, 30 days for monthly.
3. **Frame it as investment, not cost.** "We have added X, Y, Z since your last renewal. Our new pricing reflects this expanded value."
4. **Offer an annual lock-in.** "Lock in current pricing for 12 months by switching to annual billing."
5. **Start with new customers.** Raise prices for new customers first, then roll out to existing customers in cohorts.
6. **Measure churn impact.** If churn increases by less than the revenue gain from higher prices, the increase is net positive. A 5% price increase with 1% incremental churn is a clear win.

### Frequency
- Re-evaluate pricing every 6 months.
- Adjust pricing every 12-18 months for most SaaS products.
- Tie increases to product improvements, not arbitrary timelines.

## Pricing Page Best Practices

### Layout and Structure
- Display 3 tiers side by side. The middle tier (Better) should be visually emphasized.
- Use a toggle for monthly vs annual pricing. Show the annual discount as a percentage or dollar amount saved.
- Place the pricing section above the fold or within one scroll on desktop.
- Include a brief FAQ below the tiers addressing common objections (Can I switch plans? Is there a contract? What happens if I exceed my limits?).

### Copy and Messaging
- Lead with the outcome, not the feature. "Close deals faster" beats "CRM with pipeline management."
- Name tiers after the target persona or stage, not abstract concepts. "Starter, Growth, Enterprise" beats "Silver, Gold, Platinum."
- Use specific numbers over vague language. "Up to 10 users" beats "For small teams."
- Include social proof on the pricing page — logos, testimonial quotes, or "Join X companies" language.

### Conversion Optimization
- Every tier needs a CTA button. Use action-oriented labels: "Start Free Trial," "Get Started," "Talk to Sales."
- Reduce friction: do not require a credit card for free trials unless your qualification data shows it improves lead quality.
- Add a comparison table below the tier cards for users who want to see the full feature breakdown.
- Include a "Not sure which plan?" CTA that routes to sales or a quiz.

### Enterprise Tier
- Use "Contact Us" or "Talk to Sales" for enterprise pricing. Displaying a high number without context causes sticker shock.
- List enterprise-specific features prominently: SSO, SLA, dedicated support, custom contracts, security certifications.
- Include logos of enterprise customers near this tier.

## Pricing Psychology

### Anchoring
The first price a customer sees sets the reference point for all subsequent evaluations. Display the highest tier first (left to right) to make the middle tier feel affordable. Or display the middle tier as "Most Popular" to anchor expectations.

**Application:** On your pricing page, show the Enterprise tier first. The Pro tier at $49/month feels reasonable after seeing Enterprise at $199/month.

### Decoy Effect (Asymmetric Dominance)
A third option that is clearly inferior to one of the other two options makes that other option more attractive.

**Application:** If you have a Basic at $19 and Pro at $49, add a "Plus" at $39 that has fewer features than Pro. Suddenly Pro looks like the obvious choice for just $10 more.

### Charm Pricing
Prices ending in 9 or 7 ($49, $97) are perceived as significantly lower than the next round number. This works best for consumer and SMB products. For enterprise, round numbers ($50, $100, $500) signal premium positioning.

**Application:** Use $49/month for your growth tier (signals value), $500/month for enterprise (signals premium).

### Price Partitioning
Breaking a price into components makes the total feel smaller. "$29/month + $10/user" feels cheaper than "$49/month for 2 users" even though they are equivalent.

**Warning:** This can backfire if the total becomes hard to predict. Use partitioning for transparent components, not to obscure the true cost.

### Loss Aversion in Pricing
People feel losses roughly twice as strongly as equivalent gains. Frame pricing changes as "keeping" value, not "gaining" value.

**Application:** "Keep your current rate by switching to annual" is more compelling than "Save 20% with annual billing." During trials, give full access to the highest tier, then show what they will lose if they downgrade.

### The Center Stage Effect
When presented with three options, people disproportionately choose the middle one. This is why the Better tier should always be in the center position.

**Application:** Design your Good-Better-Best layout so the Better tier is physically centered and visually highlighted. 60-70% of conversions should land here.

## Freemium vs Free Trial

### Freemium
- **Use when:** Your product has a viral or network effect, the marginal cost per free user is near zero, and the product's value increases with more users in an organization.
- **Conversion benchmark:** 2-5% of free users convert to paid.
- **Risk:** Building features for free users that do not drive upgrades. Every free feature should either drive adoption (leading to paid conversion) or showcase the value of paid features.

### Free Trial
- **Use when:** Your product's value is obvious after trying it, the product requires setup or onboarding effort, and you want higher-intent leads.
- **Trial length:** 14 days is standard. 7 days for simple products, 30 days for complex ones. Shorter trials create urgency.
- **Conversion benchmark:** 10-25% of trials convert to paid.
- **Credit card required:** Yes if you want qualified leads and higher conversion rates. No if you want volume and are willing to nurture.

### Reverse Trial (Hybrid)
Give new users full premium access for 14 days, then downgrade to a free tier. This combines the low friction of freemium with the urgency of a trial. Users experience the premium value and feel loss aversion when it is taken away.

## Common Pricing Mistakes

1. **Cost-plus pricing** — Adding a margin to your costs ignores the value you deliver. A feature that costs $0.01 to serve can be worth $100/month to the customer.
2. **Competitor-matching** — Pricing relative to competitors without understanding your unique value proposition. You might be worth 3x more (or 3x less).
3. **Too many tiers** — More than 4 tiers creates decision paralysis. Simplify.
4. **No expansion path** — If your largest customer pays the same as your smallest, your pricing is broken.
5. **Underpricing to win deals** — Low prices attract price-sensitive customers who churn the fastest and demand the most support.
6. **Never changing prices** — Pricing is not a one-time decision. Revisit every 6-12 months.
7. **Hiding pricing** — Unless you are genuinely enterprise-only, hiding pricing creates friction and filters out self-serve buyers.
