---
name: product-marketing-context
description: |
  Establish product marketing foundations: ICP, positioning, messaging, and competitive landscape.
  This skill creates a product-marketing-context.md file that other skills reference.
  Trigger: user mentions "product marketing", "ICP", "ideal customer profile",
  "value proposition", "positioning", "messaging framework", "competitive landscape",
  "differentiators", "persona", "voice of customer", "use cases", "go-to-market",
  "GTM", "product positioning", "messaging", "target audience"
metadata:
  version: 1.0.0
  author: Andre Ginja
---

# Product Marketing Context

## Overview

This skill helps you build the foundational product marketing document that other marketing skills reference. The output is a `product-marketing-context.md` file containing your ICP, positioning, messaging framework, competitive landscape, and personas.

Every marketing activity — from ad copy to sales enablement to content strategy — should be grounded in these foundations. Without them, marketing efforts are disconnected and inconsistent.

## Creating the Product Marketing Context File

When a user needs to establish their product marketing foundation, guide them through each section below and compile the results into a `product-marketing-context.md` file.

### File Structure

```markdown
# Product Marketing Context

## Company Overview
- Company name:
- Product name(s):
- Category:
- Website:
- Founded:
- Stage: [Pre-revenue / Early / Growth / Scale / Mature]

## Ideal Customer Profile (ICP)
[See ICP section below]

## Customer Personas
[See Personas section below]

## Value Proposition
[See Value Proposition section below]

## Positioning Statement
[See Positioning section below]

## Messaging Framework
[See Messaging section below]

## Competitive Landscape
[See Competitive section below]

## Key Differentiators
[See Differentiators section below]

## Use Cases
[See Use Cases section below]

## Voice of Customer
[See VoC section below]

---
Last updated: [Date]
```

## Ideal Customer Profile (ICP)

### What an ICP Is (and Is Not)

- **ICP** = The type of company that gets the most value from your product and is most likely to buy, retain, and expand.
- **ICP is not** = Everyone who could use your product. Narrowing your ICP makes all marketing and sales activities more effective.

### ICP Framework

Build your ICP across these dimensions:

**Firmographic Attributes:**
| Attribute | Definition |
|-----------|-----------|
| Industry/vertical | Which industries do your best customers come from? |
| Company size | Employee count range or revenue range |
| Geography | Countries, regions, or markets served |
| Business model | B2B, B2C, DTC, SaaS, marketplace, etc. |
| Technology stack | Required or complementary technologies |
| Growth stage | Startup, growth, enterprise, public |

**Situational Attributes (Triggers):**
| Trigger | What It Means |
|---------|--------------|
| Hiring signal | Hiring for a role your product supports (e.g., hiring data engineers = need for data tools) |
| Funding round | New capital often triggers tool evaluation |
| Tech migration | Moving platforms creates buying windows |
| Regulatory change | New compliance requirements drive purchases |
| Leadership change | New CXO often re-evaluates tech stack |
| Growth milestone | Hitting 50/100/500 employees often triggers operational tool needs |

**Negative ICP (Who to Exclude):**
- Companies too small to afford or implement your product
- Industries with regulatory barriers you can't meet
- Companies with in-house alternatives and no switching motivation
- Markets where your product has consistently failed to retain customers

### ICP Scoring Exercise

To identify your ICP from existing data, score your current customers:

```
For each customer, score 1-5 on:
- Revenue contribution (1=lowest, 5=highest)
- Retention/tenure (1=churned quickly, 5=long-term)
- Expansion revenue (1=none, 5=significant upsells)
- Time to close (1=longest, 5=fastest)
- Support burden (1=highest, 5=lowest)
- Referral/advocacy (1=none, 5=active promoter)

Total score (max 30) → Rank customers → Analyze common attributes of top quartile
```

The patterns in your top-scoring customers define your ICP.

## Customer Personas

### Persona Template

Create 2-4 personas covering your key buyer and user roles:

```markdown
### Persona: [Name — e.g., "Marketing Mary"]

**Role:** [Job title(s)]
**Reports to:** [Their manager's role]
**Team size:** [How many people they manage]

**Demographics:**
- Age range: [e.g., 30-45]
- Experience level: [e.g., 8-15 years in marketing]
- Education: [e.g., Bachelor's in Business/Marketing]

**Goals:**
- [Primary professional goal]
- [Secondary professional goal]
- [Personal career aspiration related to their role]

**Pain Points:**
- [Biggest daily frustration]
- [Biggest strategic challenge]
- [What keeps them from getting promoted]

**How They Measure Success:**
- [KPI 1]
- [KPI 2]
- [KPI 3]

**Information Sources:**
- [Where they learn about new tools — podcasts, newsletters, communities]
- [Where they go for peer advice]
- [Conferences they attend]

**Role in Purchase Decision:**
- [Champion / Decision Maker / Influencer / User / Blocker]
- [Budget authority: Yes/No, up to what amount]

**Objections They'll Raise:**
- [Common objection 1]
- [Common objection 2]

**What Messaging Resonates:**
- [Value they care about most]
- [Proof they need to see]
```

### Persona Research Methods

| Method | What You Learn | Sample Size |
|--------|---------------|-------------|
| Customer interviews | Deep motivations, language, pain points | 10-15 per persona |
| Sales call recordings | Objections, questions, decision criteria | 20-30 calls |
| Support ticket analysis | Pain points, friction areas | 100+ tickets |
| Survey | Quantitative validation of qualitative findings | 50+ responses |
| G2/Gartner reviews | Competitive perception, valued features | All available |
| Job postings (for their role) | Priorities, required skills, company needs | 20-30 postings |
| LinkedIn profile analysis | Career trajectory, skills, interests | 30-50 profiles |

### Buyer vs. User Personas

In B2B, the person who buys is often not the person who uses the product daily. You need both:

- **Buyer persona**: Cares about ROI, risk, strategic alignment, vendor credibility
- **User persona**: Cares about ease of use, time savings, integration with workflow, daily reliability
- **Executive sponsor**: Cares about strategic outcomes, competitive advantage, board-level metrics

## Value Proposition

### Value Proposition Canvas

Map your product's value against customer needs:

```
Customer Side:
- Jobs to be done: [What are they trying to accomplish?]
- Pains: [What frustrates them about current solutions?]
- Gains: [What would make their life better?]

Product Side:
- Products/services: [What you offer]
- Pain relievers: [How you eliminate specific pains]
- Gain creators: [How you create specific gains]

Value Proposition = The intersection where your pain relievers and
gain creators address their most important jobs, pains, and gains.
```

### Value Proposition Formula

**Template:**
"We help [target customer] [achieve outcome] by [unique approach], so they can [ultimate benefit], unlike [alternative] which [limitation]."

**Examples:**
- "We help mid-market SaaS companies reduce customer churn by 30% through predictive health scoring, so they can grow NRR without increasing headcount, unlike manual CSM approaches which miss at-risk accounts until it's too late."
- "We help e-commerce brands increase ROAS by 40% through AI-powered creative testing, so they can scale ad spend profitably, unlike agencies which rely on gut instinct and monthly reports."

### Testing Your Value Proposition

- **The "so what" test**: After every claim, ask "so what?" If you can't answer with a concrete benefit, the claim is too vague.
- **The "who else" test**: Could a competitor say the same thing? If yes, it's not differentiated.
- **The "prove it" test**: Can you back it up with data or customer evidence? If not, it's an aspiration, not a proposition.

## Positioning Statement

### Positioning Framework

```
For [target customer]
who [statement of need or opportunity],
[Product name] is a [market category]
that [statement of key benefit].
Unlike [primary competitive alternative],
our product [statement of primary differentiation].
```

### Positioning Considerations

**Category choice matters enormously:**
- Choosing an existing category (e.g., "CRM") means you benefit from existing demand but compete on features
- Creating a new category (e.g., "Revenue Intelligence") means you define the rules but must educate the market
- Repositioning in an adjacent category (e.g., "CRM" → "Customer Platform") can differentiate without full category creation cost

**When to create a new category:**
- Your product truly doesn't fit existing categories
- You have the budget for sustained category education (typically $5M+ annually)
- The existing category has a negative perception you want to avoid
- You're first to market with a genuinely new approach

**When to play in an existing category:**
- There's established demand (people search for it)
- You have clear feature or price advantages
- You're early-stage and need quick market traction
- The category is growing and not yet dominated

## Messaging Framework

### Three-Layer Messaging Architecture

**Layer 1: Company-Level Message**
- One sentence that captures the entire value proposition
- Used in: website hero, elevator pitch, PR
- Example: "The revenue intelligence platform that turns conversation data into closed deals"

**Layer 2: Persona-Level Messages**
For each persona, customize the message:

| Persona | Primary Message | Key Benefits | Proof Point |
|---------|----------------|-------------|-------------|
| VP Sales | [Message focused on their goals] | [3 benefits] | [Relevant stat or case study] |
| Sales Rep | [Message focused on their goals] | [3 benefits] | [Relevant stat or case study] |
| CRO | [Message focused on their goals] | [3 benefits] | [Relevant stat or case study] |

**Layer 3: Use-Case-Level Messages**
For each key use case:

```
Use Case: [Name]
Headline: [One line]
Subhead: [One sentence expanding on headline]
Body: [2-3 sentences with proof]
CTA: [Specific action]
```

### Messaging Do's and Don'ts

**Do:**
- Use customer language (from interviews, reviews, support tickets)
- Lead with outcomes, not features
- Be specific: numbers, timeframes, named results
- Test messaging with actual prospects before committing
- Create a shared messaging doc that all teams reference

**Don't:**
- Use jargon your customers don't use
- Lead with features ("AI-powered" means nothing without context)
- Make unsubstantiated claims ("best-in-class," "#1 rated")
- Create messaging in isolation from sales and customer success input
- Set messaging once and never revisit (review quarterly)

## Competitive Landscape

### Competitive Analysis Framework

For each major competitor (top 3-5), document:

```markdown
### [Competitor Name]

**Overview:**
- Positioning: [How they describe themselves]
- Target market: [Who they sell to]
- Pricing model: [How they charge]
- Estimated size: [Revenue, employees, funding if known]

**Strengths:**
- [Strength 1 — be honest]
- [Strength 2]
- [Strength 3]

**Weaknesses:**
- [Weakness 1 — based on evidence, not assumption]
- [Weakness 2]
- [Weakness 3]

**Where We Win Against Them:**
- [Scenario or use case where we're stronger]
- [Feature or approach that differentiates us]

**Where They Win Against Us:**
- [Scenario or use case where they're stronger]
- [Feature we lack that they have]

**Win Rate Against Them:** [X%] (from CRM data)
**Primary Reason We Win:** [From win/loss interviews]
**Primary Reason We Lose:** [From win/loss interviews]
```

### Competitive Intelligence Sources

| Source | What You Get | Frequency |
|--------|-------------|-----------|
| Win/loss interviews | Why you won or lost specific deals | After every closed deal |
| G2, Capterra, TrustRadius reviews | User sentiment, feature gaps, strengths | Monthly review |
| Competitor websites and blogs | Messaging changes, new features, case studies | Monthly |
| Job postings | Strategic priorities (hiring for new product areas) | Quarterly |
| SEC filings (public companies) | Revenue, growth, strategy | Quarterly |
| Industry analyst reports | Market positioning, feature comparisons | Annually |
| Conference talks and webinars | Product roadmap, customer stories | As available |
| Social media and community mentions | Sentiment, common complaints | Ongoing |

## Key Differentiators

### Differentiator Validation

A real differentiator must pass three tests:

1. **True**: You can actually deliver on it consistently
2. **Relevant**: Customers care about it (it influences purchase decisions)
3. **Provable**: You have evidence — data, case studies, demos, third-party validation

### Types of Differentiators

| Type | Example | Durability |
|------|---------|-----------|
| Feature | Only platform with [capability] | Low — competitors copy features |
| Architecture | Built on [technology] enabling [unique capability] | Medium — hard to replicate |
| Data | Proprietary dataset of [X] enabling [unique insight] | High — data moats compound |
| Network | [X] users creating [network effect] | High — grows with adoption |
| Integration | Deep integration with [ecosystem] | Medium — partnerships are defensible |
| Expertise | Founded by [domain experts] with [credentials] | Medium — credibility is earned |
| Process | [Unique methodology] for [outcome] | Medium — process is defensible |
| Speed | [X]x faster to implement/deliver results | Low-Medium — efficiency gains are copyable |

### Articulating Differentiators

For each differentiator, document:
- **What**: The differentiator in one sentence
- **Why it matters**: The customer benefit it enables
- **Proof**: Data point, case study, or demo moment that proves it
- **Talk track**: How a sales rep should present it in conversation

## Use Cases

### Use Case Documentation Template

```markdown
### Use Case: [Name]

**Persona:** [Who uses this use case]
**Industry:** [Where it's most relevant]
**Problem:** [What triggers this use case]

**Current State (Without Us):**
- [How they do it today]
- [What's painful about the current approach]
- [Quantified cost or inefficiency]

**Future State (With Us):**
- [How they do it with our product]
- [What improves]
- [Quantified benefit]

**Key Features Involved:**
- [Feature 1] — enables [specific capability]
- [Feature 2] — enables [specific capability]

**Customer Example:**
[Company name] uses [Product] for [this use case] and achieved [result].

**Keywords/Search Terms:**
[Terms prospects might search when looking for this solution]
```

### Prioritizing Use Cases

Rank use cases by:
1. **Revenue impact**: Which use cases drive the most revenue?
2. **Win rate**: Which use cases have the highest win rate when positioned?
3. **Retention**: Which use cases have the strongest retention?
4. **Market size**: How large is the addressable market for each use case?

Focus marketing efforts on the top 3-5 use cases. Support the rest with documentation but don't lead with them.

## Voice of Customer (VoC)

### VoC Collection System

| Channel | What to Capture | How to Use |
|---------|----------------|-----------|
| Customer interviews | Language, priorities, unmet needs | Messaging, product roadmap |
| Sales call recordings | Objections, decision criteria, competitor mentions | Sales enablement, positioning |
| Support tickets | Pain points, feature requests, friction areas | Product improvement, content creation |
| NPS/CSAT surveys | Satisfaction drivers, detractor themes | Retention strategy, messaging |
| G2/review site reviews | Public perception, comparison criteria | Competitive positioning |
| Community and social | Organic discussion, sentiment | Brand messaging, content ideas |
| Onboarding feedback | First impressions, expectations vs. reality | Onboarding optimization |

### VoC Documentation

Maintain a running document of actual customer quotes organized by theme:

```markdown
### Theme: [e.g., "Time savings"]

**Quotes:**
- "We used to spend 4 hours every Monday pulling reports. Now it takes 10 minutes."
  — [Name], [Title], [Company]
- "My team got back 15 hours a week that we now spend on strategy instead of data entry."
  — [Name], [Title], [Company]

**Frequency:** Mentioned in 8/12 recent interviews
**Sentiment:** Strongly positive
**Use in:** Website hero, case studies, ad copy, sales deck
```

### How VoC Feeds Other Marketing Activities

- **Ad copy**: Use exact customer language in headlines and body copy
- **Website**: Mirror VoC phrases on landing pages and feature descriptions
- **Sales enablement**: Equip reps with customer quotes for each objection and use case
- **Content marketing**: Write articles addressing the themes customers mention most
- **Product marketing**: Validate positioning against what customers actually say
- **Product**: Prioritize roadmap based on frequency and severity of unmet needs

## Maintaining the Product Marketing Context

### Review Cadence

| Section | Review Frequency | Trigger for Update |
|---------|-----------------|-------------------|
| ICP | Quarterly | Customer mix shifts, new segment emerges |
| Personas | Semi-annually | New buyer role identified, major persona changes |
| Value Proposition | Quarterly | Product changes, market shifts |
| Positioning | Semi-annually | Competitive moves, category changes |
| Messaging | Quarterly | New messaging test results, VoC changes |
| Competitive Landscape | Monthly | Competitor launches, pricing changes |
| Differentiators | Quarterly | Feature parity changes, new capabilities |
| Use Cases | Quarterly | New use case validated with 3+ customers |
| VoC | Monthly | Ongoing collection |

### Distribution

Share the product marketing context document with:
- Marketing team (all functions)
- Sales team (include in onboarding)
- Customer success (for renewal and expansion conversations)
- Product team (for roadmap alignment)
- Executive team (for strategic alignment)

Store it in a central, accessible location. Version it. Never let it become a PDF that sits in someone's email.
