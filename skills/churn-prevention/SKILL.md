---
name: churn-prevention
description: |
  Reduce customer churn through prediction, prevention, and win-back strategies.
  Trigger: user mentions "churn", "churn prevention", "customer retention", "cancel",
  "cancellation flow", "save offer", "at-risk customers", "retention rate",
  "NRR", "net revenue retention", "logo churn", "revenue churn", "win-back",
  "re-engagement", "health score", "customer health", "downsell", "downgrade"
metadata:
  version: 1.0.0
  author: Andre Ginja
---

# Churn Prevention Strategy

## Understanding Churn Types

| Churn Type | Definition | Typical Range |
|------------|-----------|---------------|
| Logo Churn | % of customers who cancel in a period | 3-7% monthly (SMB SaaS), <1% monthly (Enterprise) |
| Revenue Churn (Gross) | % of MRR lost from cancellations + downgrades | 1-4% monthly |
| Revenue Churn (Net) | Gross churn minus expansion revenue | Negative is excellent (net expansion) |
| Voluntary Churn | Customer actively chooses to cancel | 60-80% of total churn |
| Involuntary Churn | Payment failure, expired card | 20-40% of total churn |

**Net Revenue Retention (NRR)** is the single most important retention metric:
- NRR = (Starting MRR + Expansion - Contraction - Churn) / Starting MRR
- Best-in-class SaaS: 120-140% NRR
- Good: 100-120% NRR
- Concerning: Below 100% NRR (you're shrinking)

## Churn Prediction Signals

### Behavioral Signals (Product Usage)

Early warning indicators ranked by predictive power:

| Signal | Risk Level | Detection Window |
|--------|-----------|-----------------|
| Zero logins in 14+ days | Critical | 2-4 weeks before churn |
| Feature usage declining 50%+ week-over-week | High | 3-6 weeks before churn |
| Support ticket volume spike | High | 2-4 weeks before churn |
| Key feature never adopted | Medium-High | 30-60 days into lifecycle |
| Team seats removed | Medium | 2-4 weeks before churn |
| Billing page visited without changes | Medium | 1-2 weeks before churn |
| Data export or API usage spike | Medium | 1-3 weeks before churn |
| Downgrade inquiry or pricing page visit | Medium | 1-4 weeks before churn |
| Reduced session duration | Low-Medium | 4-8 weeks before churn |
| Integration disconnected | Medium-High | 2-4 weeks before churn |

### Relationship Signals

- **Champion left the company** — The person who bought your product changed roles or companies. Track this via LinkedIn Sales Navigator alerts or ZoomInfo.
- **No executive sponsor** — Accounts without a senior stakeholder engaged have 3x higher churn.
- **NPS detractor** — Customers scoring 0-6 on NPS churn at 2-4x the rate of promoters.
- **Unresolved support tickets** — Open tickets older than 48 hours correlate with churn.
- **No QBR or check-in in 90+ days** — Disengagement from the relationship is a leading indicator.

### Business Signals

- **Funding round or acquisition** — New leadership may reevaluate all vendor contracts.
- **Layoffs** — Reduced headcount often leads to tool consolidation.
- **Competitor mentions in support tickets** — Direct signal of evaluation.
- **Contract renewal approaching** — 60-90 days before renewal is the highest-risk window.

## Customer Health Scoring

### Building a Health Score Model

Create a composite score from 0-100 using weighted categories:

```
Health Score = (Product Usage * 0.35) + (Engagement * 0.25) +
              (Support * 0.20) + (Relationship * 0.20)
```

**Product Usage Score (0-100, weight: 35%)**
- Breadth: % of key features used (vs. available)
- Depth: Frequency of usage vs. expected baseline
- Recency: Days since last meaningful action
- Adoption velocity: Speed of new feature adoption

**Engagement Score (0-100, weight: 25%)**
- Login frequency vs. baseline
- Number of active users vs. licensed seats
- Time spent in product per session
- Content consumption (help docs, webinars, emails opened)

**Support Score (0-100, weight: 20%)**
- CSAT from recent tickets (invert: lower CSAT = lower score)
- Ticket volume trend (sudden spikes lower the score)
- Time to resolution
- Escalation count

**Relationship Score (0-100, weight: 20%)**
- Executive sponsor identified and engaged
- QBR/check-in cadence met
- Multi-threaded (contacts across departments)
- NPS/CSAT survey responses

### Health Score Tiers

| Score | Tier | Action |
|-------|------|--------|
| 80-100 | Healthy | Expand: upsell, cross-sell, referral ask |
| 60-79 | Neutral | Monitor: increase touchpoints, drive feature adoption |
| 40-59 | At-Risk | Intervene: CSM outreach, success plan, executive sponsor |
| 0-39 | Critical | Rescue: immediate escalation, save offer, executive call |

### Operationalizing Health Scores

- Calculate and update scores daily or weekly (automated, not manual)
- Surface scores in your CRM and CS platform (Gainsight, ChurnZero, Vitally, or custom)
- Set automated alerts when accounts drop tiers
- CSM dashboard should sort accounts by health score, lowest first
- Track health score trends, not just snapshots — a score of 65 dropping from 85 is more urgent than a stable 55

## Cancel Flow Optimization

### Cancel Flow Architecture

The goal is not to trap customers — it is to understand their reason, offer alternatives, and make it easy to return.

**Step 1: Reason Collection (Required)**
Present 5-7 cancellation reasons as selectable options:

1. Too expensive / budget constraints
2. Not using it enough
3. Missing features I need
4. Switching to a competitor
5. Technical issues / poor experience
6. Business closed / project ended
7. Other (free text)

**Step 2: Dynamic Save Offer (Based on Reason)**

| Reason | Save Offer |
|--------|-----------|
| Too expensive | Offer 20-40% discount for 3 months, or downgrade to lower tier |
| Not using enough | Offer pause (1-3 months) instead of cancel, or guided onboarding |
| Missing features | Share roadmap timeline if feature is planned, offer workaround |
| Switching to competitor | Offer competitive comparison, premium support, or custom pricing |
| Technical issues | Escalate to engineering, offer dedicated support session |
| Business/project ended | Offer pause, leave on good terms for future return |

**Step 3: Confirmation with Soft Off-Ramp**
- "Your cancellation is confirmed effective [date]"
- "You'll retain access until [billing period end]"
- "Changed your mind? You can reactivate anytime at [link]"
- "We'd love to have you back — here's 30% off if you return within 90 days"

### Cancel Flow Performance Benchmarks

- **Save rate**: 10-25% of users who enter the cancel flow should be saved
- **Reason completion rate**: 90%+ (make it required but easy)
- **Discount acceptance rate**: 15-30% of those shown an offer
- **Pause acceptance rate**: 20-35% of those offered a pause

### What Not to Do

- Do not hide the cancel button — it creates resentment and negative reviews
- Do not require phone calls to cancel (unless enterprise with contractual terms)
- Do not make the flow more than 3-4 steps
- Do not offer the same save offer to everyone — personalization doubles save rates
- Do not ignore the data — pipe cancellation reasons to product and CS teams weekly

## Save Offers and Downgrades

### Offer Hierarchy (Present in Order)

1. **Pause subscription** — 1-3 month pause, no charge, data preserved. Best save rate.
2. **Downgrade to lower tier** — Reduce cost while keeping the customer. Preserves logo.
3. **Discount (time-limited)** — 20-40% off for 2-3 months. Use for price-sensitive customers.
4. **Extended trial of premium features** — If they haven't experienced full value, unlock features for 30 days.
5. **Dedicated support session** — Personal walkthrough to solve their specific pain point.

### Downgrade Strategy

- Design your pricing tiers so there's always a step-down option
- A customer paying $29/month is infinitely more valuable than a churned customer
- Track downgraded customers separately — many re-expand within 6 months
- Make upgrading back effortless (one click, immediate access)

### Financial Framework for Discounts

Calculate the maximum discount that's still profitable:
- If customer LTV is $2,400 and CAC is $800, you can offer up to 33% discount and still be profitable
- A 3-month discount costs far less than acquiring a new customer
- Track discount cohorts: do discounted customers churn at renewal? Adjust strategy accordingly.

## At-Risk Customer Identification and Intervention

### Automated Playbooks

**Playbook 1: Engagement Drop**
- Trigger: Login frequency drops 50%+ from baseline for 2 consecutive weeks
- Action: Automated email with usage tips, followed by CSM outreach after 3 days if no response
- Escalation: If no engagement after 2 weeks, manager-level outreach

**Playbook 2: Support Escalation**
- Trigger: 3+ support tickets in 7 days, or CSAT below 3/5 on any ticket
- Action: CSM reaches out same day. Schedule a call to address systemic issues.
- Escalation: Director-level call if unresolved in 1 week

**Playbook 3: Renewal Risk**
- Trigger: 90 days before contract renewal + health score below 60
- Action: CSM builds success plan, schedules QBR, prepares ROI report
- Escalation: Executive sponsor engagement at 60 days if no improvement

**Playbook 4: Champion Change**
- Trigger: Primary contact leaves company (detected via email bounce, LinkedIn, or ZoomInfo)
- Action: Immediate outreach to identify new stakeholder, re-onboard, share value documentation
- Escalation: Account executive re-engagement if no new champion identified in 2 weeks

## Re-Engagement Campaigns

### Email Sequences for At-Risk Customers

**Sequence 1: Dormant User Re-Engagement (no login 14+ days)**

| Day | Email | Subject Line Example |
|-----|-------|---------------------|
| 1 | Value reminder | "Your [feature] insights are waiting" |
| 4 | Tip/tutorial | "3 ways [Customer Type] use [Product] to [Result]" |
| 8 | Social proof | "[Similar Company] achieved [Result] — here's how" |
| 14 | Direct ask | "Can we help? 15-min call to get you back on track" |
| 21 | Final nudge | "We miss you — here's what's new in [Product]" |

**Sequence 2: Post-Downgrade Nurture**

| Day | Email | Goal |
|-----|-------|------|
| 7 | Check-in | Confirm downgrade is working for them |
| 30 | Feature highlight | Show value of features in their current tier |
| 60 | Case study | Success story from similar customer |
| 90 | Upgrade offer | Limited-time incentive to return to higher tier |

### In-App Re-Engagement

- **Feature spotlights**: Surface unused features via tooltips or banners
- **Progress indicators**: "You've used 2 of 8 available features — explore more"
- **Personalized dashboards**: Show ROI metrics — "You've saved X hours this month"
- **Win-back modals**: When a lapsed user returns, welcome them and offer a guided path

## Exit Surveys

### Survey Design

Keep exit surveys to 3-5 questions maximum:

1. **Primary reason for leaving** (single select from predefined list)
2. **What would have made you stay?** (open text — this is the most valuable question)
3. **Would you recommend us to others?** (NPS scale 0-10)
4. **What will you use instead?** (single select: competitor names + "nothing" + "built in-house")
5. **Would you consider returning in the future?** (Yes / Maybe / No)

### Analyzing Exit Survey Data

- Aggregate monthly and look for trends — if "too expensive" jumps from 15% to 30%, you have a pricing problem
- Cross-reference with customer segments — are enterprise and SMB churning for different reasons?
- Share findings with product (feature gaps), engineering (technical issues), and sales (expectation mismatches) weekly
- Track "what would have made you stay" responses to identify high-impact retention investments

## Involuntary Churn Prevention

Involuntary churn (failed payments) is often 20-40% of total churn and is almost entirely preventable.

### Dunning Best Practices

**Pre-failure prevention:**
- Send card expiration reminders 30, 14, and 7 days before expiry
- Offer multiple payment methods (credit card, ACH, PayPal)
- Use account updater services (Stripe, Braintree have these built in)

**Post-failure recovery:**
- Retry failed payments: Day 1, Day 3, Day 5, Day 7 (4 retries over 7 days)
- Retry at different times of day — some failures are temporary bank-side holds
- Send a sequence: friendly notification (Day 1), reminder (Day 3), urgency (Day 5), final notice (Day 7)
- Keep the account active during the retry window — do not lock them out immediately

**Recovery rate benchmarks:**
- Pre-expiry card updates: 30-50% of at-risk cards updated
- Smart retry logic: recovers 15-25% of failed payments
- Dunning emails: recover an additional 10-20%
- Total involuntary churn recovery: 40-70% with a good system

## Retention Metrics Dashboard

### Core Metrics to Track

| Metric | Formula | Frequency |
|--------|---------|-----------|
| Logo Churn Rate | Customers lost / Starting customers | Monthly |
| Gross Revenue Churn | MRR lost / Starting MRR | Monthly |
| Net Revenue Retention | (Starting MRR + Expansion - Contraction - Churn) / Starting MRR | Monthly, reported annually |
| Customer Lifetime Value | ARPU / Monthly Churn Rate | Monthly |
| Expansion Rate | Expansion MRR / Starting MRR | Monthly |
| Save Rate | Saved customers / Cancel-initiated customers | Monthly |
| Time to First Value | Days from signup to first key action | Ongoing |
| DAU/MAU Ratio | Daily active / Monthly active | Weekly |

### Cohort Analysis

Track retention by signup cohort to understand if retention is improving over time:

```
Cohort  | M1   | M2   | M3   | M6   | M12
--------|------|------|------|------|------
Jan '24 | 92%  | 85%  | 80%  | 72%  | 65%
Apr '24 | 94%  | 88%  | 84%  | 77%  | --
Jul '24 | 95%  | 90%  | 86%  | --   | --
Oct '24 | 93%  | 87%  | --   | --   | --
```

If later cohorts retain better, your product and onboarding improvements are working. If curves look the same or worse, your retention investments aren't landing.

### Segmented Churn Analysis

Always break churn down by:
- **Plan tier**: Free vs. paid, SMB vs. enterprise
- **Acquisition channel**: Organic vs. paid vs. referral vs. sales-led
- **Industry/vertical**: Some segments inherently churn more
- **Tenure**: First 90 days vs. 90-365 days vs. 365+ days
- **Company size**: Solopreneurs churn very differently from 500-person companies

This segmentation reveals where to focus. If SMB monthly churn is 8% but enterprise is 0.5%, your SMB onboarding or pricing needs attention, not your product broadly.
