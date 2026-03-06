---
name: revops
description: |
  Revenue operations strategy covering lead management, pipeline, and data-driven growth.
  Trigger: user mentions "RevOps", "revenue operations", "lead scoring", "pipeline",
  "lead routing", "handoff", "MQL", "SQL", "data hygiene", "CRM", "attribution",
  "forecasting", "deal desk", "revenue dashboard", "lead management",
  "marketing to sales handoff", "pipeline velocity", "conversion rates"
metadata:
  version: 1.0.0
  author: Andre Ginja
---

# Revenue Operations

## The RevOps Framework

Revenue Operations aligns marketing, sales, and customer success around shared metrics, processes, and technology to drive predictable revenue growth.

### Core RevOps Pillars

1. **Process** — Standardized workflows for lead management, pipeline, handoffs, and renewals
2. **Data** — Clean, unified data across systems with consistent definitions
3. **Technology** — Integrated tech stack that eliminates silos and enables automation
4. **Insights** — Reporting and analytics that drive decision-making at every level

### The Revenue Funnel (Standardized Definitions)

| Stage | Definition | Owner | Typical Conversion |
|-------|-----------|-------|--------------------|
| Visitor | Anonymous site visitor | Marketing | — |
| Lead | Known contact (form fill, signup) | Marketing | 5-15% of visitors |
| MQL | Meets marketing qualification criteria | Marketing | 15-30% of leads |
| SAL | Sales accepted, working the lead | Sales | 60-80% of MQLs |
| SQL | Sales qualified, real opportunity | Sales | 40-60% of SALs |
| Opportunity | Active deal in pipeline | Sales | 70-90% of SQLs |
| Closed Won | Revenue booked | Sales | 15-30% of opportunities |
| Customer | Active account | CS | — |

**Critical rule**: Marketing and sales must agree on these definitions before building anything else. Misaligned definitions are the #1 source of revenue team friction.

## Lead Scoring Models

### Demographic/Firmographic Scoring (Fit Score)

Score leads based on how closely they match your ideal customer profile:

| Attribute | High Fit (+) | Medium Fit | Low Fit (-) |
|-----------|-------------|------------|-------------|
| Company Size | 50-500 employees | 10-49 or 501-2000 | <10 or >2000 |
| Industry | SaaS, FinTech | Technology broadly | Government, Education |
| Job Title | VP Marketing, CMO | Director, Manager | Intern, Student |
| Revenue | $5M-$100M | $1M-$5M | <$1M |
| Geography | US, UK, Canada | EU, Australia | Restricted regions |

**Scoring example:**
- Perfect fit company size: +20 points
- Target industry: +15 points
- Decision-maker title: +25 points
- Target geography: +10 points
- Non-target attributes: 0 or negative points

### Behavioral Scoring (Interest Score)

Score leads based on engagement actions:

| Action | Points | Decay |
|--------|--------|-------|
| Requested demo | +30 | None |
| Visited pricing page | +20 | -5 per week |
| Downloaded case study | +15 | -3 per week |
| Attended webinar | +15 | -3 per week |
| Opened 3+ emails in a week | +10 | -2 per week |
| Visited blog post | +3 | -1 per week |
| Unsubscribed from emails | -30 | None |
| Bounced email | -20 | None |
| No activity in 30 days | -15 | Recurring |

**Point decay is essential** — a lead who was active 6 months ago is not the same as one active today. Implement weekly score decay on time-sensitive actions.

### Combining Fit + Interest

Use a matrix to determine the lead's status:

```
                    Interest Score
                  Low    Medium    High
Fit Score  High | MQL   | MQL    | SQL-ready
           Med  | Lead  | MQL    | MQL
           Low  | Cold  | Lead   | Lead (nurture)
```

### Lead Scoring Maintenance

- Review and recalibrate scoring monthly for the first quarter, then quarterly
- Compare scored leads against actual closed-won deals — adjust weights based on what actually predicts revenue
- Remove or reduce weight for actions that don't correlate with conversion
- Set a score threshold for MQL that produces a SAL acceptance rate of at least 60% — if sales rejects more than 40% of MQLs, your scoring is too loose

## Lead Routing

### Routing Logic

Route leads based on a priority hierarchy:

1. **Existing account match** — Route to the account owner (always check this first)
2. **Territory** — Geographic or named-account territory assignment
3. **Segment** — Enterprise vs. mid-market vs. SMB based on company size/revenue
4. **Product interest** — Route to specialist reps based on product line
5. **Round-robin** — Equal distribution among reps in the assigned segment
6. **Capacity-based** — Weight distribution by current pipeline load

### Speed-to-Lead

Response time is the single largest controllable factor in lead conversion:

| Response Time | Conversion Impact |
|---------------|-------------------|
| Under 5 minutes | 8x more likely to qualify |
| 5-30 minutes | 4x more likely |
| 30-60 minutes | 2x more likely |
| Over 1 hour | Baseline |
| Over 24 hours | Essentially cold |

**Implementation:**
- Set SLA: First outreach within 5 minutes for demo requests, 1 hour for content downloads
- Use automated alerts (Slack, email, SMS) when a hot lead enters the system
- Implement auto-assignment so leads never sit unassigned
- Track and report on speed-to-lead weekly; make it a rep-level metric
- Have a failover: if the assigned rep doesn't respond in 15 minutes, re-route to next available rep

### Lead Routing Rules Engine

Build routing logic in this order of evaluation:

```
1. Is this an existing customer? → Route to account owner
2. Is this a named/target account? → Route to assigned rep
3. Is company size > 500 employees? → Enterprise team
4. Is company size 50-500? → Mid-market team
5. Is company size < 50? → SMB/self-serve track
6. Within segment, round-robin by availability
```

Document your routing rules and review quarterly. Routing errors (leads going to the wrong rep) are a silent revenue killer.

## Marketing-to-Sales Handoff

### The Handoff Process

**Step 1: Marketing qualifies the lead (MQL)**
- Lead meets scoring threshold
- Marketing enriches the lead record with all available data

**Step 2: Notification and assignment**
- Lead is routed to sales rep via CRM automation
- Rep receives notification with lead context: source, score, pages visited, content consumed, company info

**Step 3: Sales accepts or rejects (SAL)**
- Rep has 24-48 hours to accept and begin outreach, or reject with a reason
- Rejection reasons are categorized and tracked: wrong ICP, bad data, already in pipeline, not ready

**Step 4: Sales qualifies (SQL)**
- Rep confirms BANT/MEDDIC/SPICED criteria through conversation
- Opportunity is created in CRM with stage, close date, and amount

**Step 5: Feedback loop**
- Sales provides feedback on lead quality weekly
- Marketing adjusts scoring, targeting, and content based on feedback
- Monthly alignment meeting reviews MQL-to-SQL conversion rate by source

### Handoff Data Requirements

Every lead handed to sales must include:

| Field | Source | Priority |
|-------|--------|----------|
| Full name | Form / enrichment | Required |
| Email (verified) | Form | Required |
| Company name | Form / enrichment | Required |
| Company size | Enrichment (Clearbit, ZoomInfo) | Required |
| Job title | Form / enrichment | Required |
| Lead source | UTM / form | Required |
| Lead score | Scoring model | Required |
| Pages visited (last 10) | Website tracking | Important |
| Content downloaded | Marketing automation | Important |
| Previous interactions | CRM history | Important |
| Phone number | Form / enrichment | Nice to have |
| Technology stack | Enrichment | Nice to have |

### SLA Framework

Define mutual SLAs between marketing and sales:

**Marketing commits to:**
- Deliver X MQLs per month by segment
- MQL-to-SAL acceptance rate of at least 60%
- Lead data completeness of at least 85% (required fields populated)

**Sales commits to:**
- First outreach within [SLA hours] of assignment
- Accept or reject MQLs within 48 hours
- Provide rejection reasons for every rejected MQL
- Log all activities and outcomes in CRM

## Data Hygiene

### The Cost of Bad Data

- 30% of CRM data decays annually (people change jobs, companies merge, emails bounce)
- Sales reps spend 5-10 hours per week on data-related tasks when hygiene is poor
- Bad data compounds: it corrupts reporting, breaks automation, and erodes trust in the system

### Data Hygiene Program

**Daily (automated):**
- Deduplicate new records on creation (match on email, domain, or company name + name)
- Validate email addresses on form submission (syntax + MX record check)
- Standardize fields on input (country, state, industry → picklist values)

**Weekly (automated + manual):**
- Merge duplicate contacts and companies flagged by dedup rules
- Update lead scores and lifecycle stages
- Flag records with missing required fields

**Monthly:**
- Bounce list cleanup — remove hard bounces from all lists
- Stale lead review — leads with no activity in 90+ days get re-scored or archived
- Job title standardization — normalize free-text titles to standard categories
- Enrichment refresh — re-enrich top accounts to catch personnel changes

**Quarterly:**
- Full CRM audit — % of records with complete required fields
- Attribution data validation — spot-check 20 recent closed-won deals for accurate source tracking
- Integration health check — verify all data flows between systems
- Process compliance audit — are reps following CRM entry standards?

### Data Quality Metrics

| Metric | Target | Check Frequency |
|--------|--------|-----------------|
| Record completeness (required fields) | >90% | Monthly |
| Duplicate rate | <5% | Monthly |
| Email bounce rate | <2% | Weekly |
| Attribution coverage (source known) | >95% | Monthly |
| Stale records (no activity 90d+) | <20% | Quarterly |

## CRM Optimization

### CRM Architecture Principles

1. **Objects**: Leads, Contacts, Accounts, Opportunities, Activities — map your revenue process to these
2. **Required fields**: Minimize to what's essential at each stage. Too many required fields = reps skip them or enter junk.
3. **Picklists over free text**: Standardize wherever possible for clean reporting
4. **Automation**: Auto-populate fields, auto-create tasks, auto-advance stages when criteria are met
5. **Validation rules**: Prevent bad data at entry (e.g., opportunity can't move to "Closed Won" without a close date and amount)

### Opportunity Stage Definitions

| Stage | Criteria | Probability | Required Fields |
|-------|----------|------------|-----------------|
| Discovery | Initial meeting held, pain identified | 10% | Contact, company, source |
| Qualification | BANT/MEDDIC confirmed | 20% | Budget range, timeline, decision maker |
| Solution | Demo/proposal delivered | 40% | Use case, requirements |
| Evaluation | Active evaluation, stakeholders engaged | 60% | Competition, evaluation criteria |
| Negotiation | Terms and pricing discussed | 80% | Proposed amount, contract terms |
| Closed Won | Signed contract, revenue booked | 100% | Final amount, close date, contract |
| Closed Lost | Deal lost | 0% | Loss reason (required) |

### CRM Hygiene Automation

Automate these in your CRM:
- Create a task when an opportunity has no activity for 14+ days
- Alert manager when deal is in a stage for longer than the average stage duration
- Auto-close stale opportunities (no activity for 60+ days in early stages)
- Auto-update lead lifecycle stage when scoring threshold is reached
- Trigger enrichment when a new account is created

## Reporting and Dashboards

### Executive Dashboard (Weekly Review)

| Metric | Purpose |
|--------|---------|
| Pipeline generated (this week / MTD / QTD) | Are we building enough pipe? |
| Pipeline coverage ratio | Pipeline / Quota target (3-4x is healthy) |
| Win rate (by segment, by source) | Are we closing effectively? |
| Average deal size | Trend up or down? |
| Sales cycle length | Getting faster or slower? |
| Revenue forecast (weighted) | Are we going to hit the number? |
| MQL → SQL conversion rate | Is marketing sending quality? |
| Speed-to-lead average | Are we responding fast enough? |

### Marketing Performance Dashboard

| Metric | Purpose |
|--------|---------|
| Leads by source | Where is volume coming from? |
| MQLs by source | Where is quality coming from? |
| Cost per MQL | Efficiency by channel |
| MQL → Opportunity rate | Which sources produce pipeline? |
| Influenced pipeline ($) | Marketing's impact on active deals |
| Campaign ROI | Return on specific campaign investments |

### Pipeline Dashboard

| Metric | Purpose |
|--------|---------|
| Pipeline by stage | Where are deals stuck? |
| Stage-to-stage conversion rates | Where is the biggest drop-off? |
| Average days in stage | Identify bottlenecks |
| Pipeline velocity | (Opportunities x Win Rate x Avg Deal Size) / Cycle Length |
| Aging deals | Deals in stage longer than average |

## Forecasting

### Forecast Categories

| Category | Definition |
|----------|-----------|
| Commit | Rep is highly confident (90%+). Would bet their commission on it. |
| Best Case | Likely to close but has risk factors. 60-80% confidence. |
| Pipeline | Active opportunity, too early to predict. 20-50% confidence. |
| Upside | Possible but unlikely this period. <20% confidence. |

### Forecast Accuracy

- Compare forecast to actuals every quarter
- Track forecast accuracy by rep — some reps are consistently optimistic, others conservative
- Apply historical accuracy adjustments: if a rep's commits close at 85%, apply that factor
- Triangulate: combine rep-level forecasts with historical conversion rates and pipeline coverage analysis

### Pipeline Coverage Guidelines

| Business Type | Pipeline Coverage Needed |
|---------------|------------------------|
| Transactional (short cycle) | 2-3x quota |
| Mid-market (30-90 day cycle) | 3-4x quota |
| Enterprise (90-180 day cycle) | 4-5x quota |
| New market / new product | 5-6x quota |

If coverage is below target, it's a marketing and SDR pipeline generation problem. If coverage is adequate but win rate is low, it's a sales effectiveness problem.

## Attribution

### Attribution Models

| Model | How It Works | Best For |
|-------|-------------|----------|
| First Touch | 100% credit to first interaction | Understanding demand generation sources |
| Last Touch | 100% credit to last interaction before conversion | Understanding what closes deals |
| Linear | Equal credit across all touchpoints | Fair distribution, but obscures impact |
| Time Decay | More credit to recent touchpoints | Long sales cycles |
| U-Shaped | 40% first, 40% last, 20% split among middle | Balanced view of create + close |
| W-Shaped | 30% first, 30% MQL, 30% opportunity, 10% middle | Full-funnel B2B marketing |
| Data-Driven | Algorithmic based on actual conversion data | Mature organizations with large datasets |

**Recommendation:** Start with U-shaped for B2B or first-touch for early-stage companies. Move to W-shaped or data-driven as you mature.

### Attribution Implementation

- Tag every touchpoint: UTM parameters on all links, hidden fields on forms, referral tracking
- Track both self-reported attribution ("How did you hear about us?") and system-tracked attribution — they tell different stories
- Attribution is directionally useful, not precisely accurate — use it for budget allocation decisions, not proof of exact ROI
- Review attribution data monthly and adjust channel mix quarterly

## Deal Desk Processes

### When You Need a Deal Desk

Implement a deal desk when:
- Revenue exceeds $5M ARR
- You have 3+ pricing tiers or custom pricing
- Multi-year deals or enterprise contracts are common
- Discounting needs governance

### Deal Desk Responsibilities

1. **Pricing approval** — Non-standard pricing requires deal desk review and approval
2. **Discount governance** — Define discount authority by role (rep: up to 10%, manager: up to 20%, VP: up to 30%, deal desk: custom)
3. **Contract review** — Non-standard terms reviewed for risk and precedent
4. **Revenue recognition** — Ensure deal structure aligns with accounting requirements
5. **CPQ management** — Configure-price-quote tool administration and accuracy

### Discount Approval Matrix

| Discount Level | Approver | Justification Required |
|---------------|----------|----------------------|
| 0-10% | Sales rep | None (within standard authority) |
| 11-20% | Sales manager | Competitive pressure or multi-year commitment |
| 21-30% | VP Sales | Strategic account, documented competitor pricing |
| 31%+ | Deal desk + Finance | Full business case with LTV analysis |

### Deal Desk SLAs

- Standard pricing approval: 4 hours
- Custom pricing or non-standard terms: 24 hours
- Complex enterprise deals: 48 hours
- Escalation path if SLA is missed
