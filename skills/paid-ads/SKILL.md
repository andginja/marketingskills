---
name: paid-ads
description: |
  Paid advertising strategy and execution across Google Ads, Meta Ads, and LinkedIn Ads.
  Trigger: user mentions "paid ads", "PPC", "Google Ads", "Meta Ads", "Facebook Ads",
  "LinkedIn Ads", "ad campaigns", "ROAS", "paid media", "SEM", "paid search",
  "display ads", "Performance Max", "retargeting", "remarketing", "ad spend",
  "bidding strategy", "cost per acquisition", "CPA optimization"
metadata:
  version: 1.0.0
  author: Andre Ginja
---

# Paid Advertising Strategy and Execution

## Platform Selection Framework

Choose your platform based on intent type and audience behavior:

| Platform | Best For | Avg CPC Range | Intent Level |
|----------|----------|---------------|--------------|
| Google Search | High-intent demand capture | $1-$8 | Highest |
| Google Display | Awareness, retargeting | $0.20-$2 | Low |
| Performance Max | Full-funnel automation | Varies | Mixed |
| Meta (FB/IG) | Demand generation, B2C, DTC | $0.50-$3 | Low-Medium |
| LinkedIn | B2B, high-ACV products | $5-$15 | Medium |

### Decision Matrix

- **Known demand exists** (people search for your solution) → Start with Google Search
- **Category creation needed** (people don't know they need you) → Start with Meta
- **B2B with ACV > $10K** → LinkedIn for precision targeting, Google Search for intent capture
- **E-commerce / DTC** → Meta + Google Shopping / Performance Max
- **Local business** → Google Search + Local Service Ads

## Google Ads

### Search Campaign Structure

Use the SKAG-evolved approach (themed ad groups with tight keyword clusters):

```
Campaign: [Product/Service Category]
  Ad Group: [Specific Theme A]
    Keywords: 3-7 closely related terms
    Ads: 3 responsive search ads
    Extensions: sitelinks, callouts, structured snippets
  Ad Group: [Specific Theme B]
    ...
```

**Keyword match type strategy:**
- Start with phrase match and exact match for control
- Add broad match only after you have conversion data (50+ conversions) for Smart Bidding to optimize
- Always run a negative keyword list — review search terms weekly for the first month, biweekly after

**Responsive Search Ads (RSAs) best practices:**
- Pin your strongest headline to Position 1
- Write 10-15 unique headlines covering: keyword, benefit, CTA, social proof, urgency
- Write 4 descriptions: feature-focused, benefit-focused, CTA-focused, trust-focused
- Use keyword insertion sparingly — only where it reads naturally

### Performance Max Campaigns

Performance Max works best when you feed it strong signals:

1. **Asset groups** — Create separate asset groups per product line or audience segment
2. **Audience signals** — Add custom segments (search terms, URLs), your customer lists, and in-market audiences
3. **Creative assets** — Provide at least 5 images, 5 headlines, 5 descriptions, and 1-2 videos
4. **URL expansion** — Turn OFF if you want tight landing page control; turn ON for e-commerce with many SKUs
5. **Exclude brand terms** — Add brand exclusions so PMax doesn't cannibalize cheap brand traffic

### Display Campaign Usage

Use display campaigns primarily for:
- **Retargeting** — Show ads to site visitors who didn't convert (use 30/60/90 day windows)
- **Awareness** — Reach in-market audiences with strong creative, but expect low direct conversion rates
- **Exclusions matter** — Exclude mobile apps (appspot.com, adsenseformobileapps.com), parked domains, and irrelevant placements weekly

## Meta Ads (Facebook and Instagram)

### Campaign Structure (Post-iOS 14.5)

Use the Consolidated Campaign Structure to maximize signal density:

```
Campaign: [Objective - e.g., Purchases]
  Ad Set 1: Broad (no targeting, let Meta optimize)
    Ads: 3-5 creatives
  Ad Set 2: Lookalike 1% (from purchasers)
    Ads: 3-5 creatives
  Ad Set 3: Retargeting (website visitors 1-30d)
    Ads: 3-5 creatives
```

**Key principles:**
- Use Advantage+ Shopping Campaigns (ASC) for e-commerce — they outperform manual campaigns in most cases
- Consolidate rather than fragment — Meta's algorithm needs 50 conversions per ad set per week to exit learning phase
- Set budget at campaign level with Advantage Campaign Budget (formerly CBO)
- Use UTM parameters for every ad — do not rely on Meta's attribution alone

### Audience Strategy

**Prospecting (70-80% of budget):**
- Broad targeting (age, gender, country only) works when you have strong creative and sufficient pixel data
- Interest stacking: combine 3-5 related interests into one ad set rather than splitting them
- Lookalike audiences: 1% from purchasers or high-value customers, 1-3% for scale

**Retargeting (20-30% of budget):**
- Tier 1 (highest intent): Add to cart, initiated checkout — last 7 days
- Tier 2: Product page viewers — last 14 days
- Tier 3: All site visitors — last 30 days
- Tier 4: Engaged with social content — last 60 days
- Exclude purchasers from all retargeting (or create a separate upsell campaign)

### Creative Guidelines for Meta

- **Hook in first 3 seconds** — the scroll-stopping moment determines everything
- **Aspect ratios**: 9:16 for Stories/Reels, 1:1 for Feed, 4:5 for maximum feed real estate
- **UGC-style content** outperforms polished brand creative for most DTC brands
- **Static vs. video**: Test both. Statics are cheaper to produce and often match video performance
- **Ad copy formula**: Pain point → Solution → Social proof → CTA

## LinkedIn Ads

### When LinkedIn Makes Sense

LinkedIn's high CPCs ($5-$15) are justified when:
- Your ACV (annual contract value) exceeds $5,000
- You need to reach specific job titles, company sizes, or industries
- Your sales cycle involves multiple stakeholders
- Content marketing is a core strategy (Sponsored Content performs well)

### Campaign Setup

**Targeting layers (pick 2-3 maximum):**
- Job title OR job function + seniority (don't use both title and function)
- Company size
- Industry
- Skills (useful for technical roles)
- Member groups (highly engaged audiences)

**Audience size:** Aim for 50,000-500,000 members per campaign. Below 50K is too narrow for optimization; above 500K is too broad.

**Ad formats ranked by performance:**
1. Single Image Sponsored Content — best all-around performer
2. Document Ads — high engagement for educational content
3. Video Ads — strong for brand awareness
4. Conversation Ads (InMail) — good for event registration, demos
5. Text Ads — cheap clicks but low conversion rate

### LinkedIn-Specific Tips

- Lead Gen Forms convert 2-3x better than landing pages (less friction, auto-filled data)
- Run always-on campaigns rather than flighting — LinkedIn's algorithm needs 1-2 weeks to optimize
- Use company exclusion lists to remove current customers and competitors
- Retargeting on LinkedIn: website visitors, video viewers, Lead Gen Form openers

## Bidding Strategies

### Google Ads Bidding Progression

1. **Start**: Manual CPC or Maximize Clicks (with a max CPC cap) — gather data
2. **After 15-30 conversions**: Switch to Maximize Conversions
3. **After 30-50 conversions**: Switch to Target CPA or Target ROAS
4. **Scale**: Use portfolio bid strategies across related campaigns

**Never start with Target CPA/ROAS** without conversion history — the algorithm has no signal to optimize toward.

### Meta Ads Bidding

- **Cost cap**: Set this to your target CPA. Meta will try to stay below it but may limit delivery.
- **Bid cap**: Hard ceiling on what Meta bids per auction. Use only when you have deep experience.
- **Lowest cost (no cap)**: Default and usually best for most advertisers. Let Meta find the cheapest conversions.
- **Minimum ROAS**: Set a floor for purchase campaigns. Useful for e-commerce with varied AOVs.

## Budget Allocation Framework

### The 70/20/10 Rule

- **70%** — Proven campaigns and channels that deliver consistently
- **20%** — Scaling tests (new audiences, new ad formats, adjacent keywords)
- **10%** — Experiments (new platforms, radical creative concepts, emerging formats)

### Budget by Funnel Stage

| Stage | Budget Share | KPI |
|-------|-------------|-----|
| Top of Funnel (awareness) | 20-30% | CPM, reach, video views |
| Middle of Funnel (consideration) | 10-20% | CPC, engagement, lead cost |
| Bottom of Funnel (conversion) | 50-60% | CPA, ROAS, conversion rate |

Adjust these ratios based on your business maturity. Early-stage companies need more top-of-funnel; established brands can weight toward bottom-of-funnel.

## Ad Copy Best Practices

### Headline Frameworks

1. **Benefit-first**: "Get [Desired Outcome] Without [Common Pain]"
2. **Number-driven**: "[X]% of [Audience] [Achieve Result] With [Product]"
3. **Question-based**: "Still [Doing Painful Thing]? There's a Better Way"
4. **Social proof**: "Join [X,000] [Audience Type] Who [Achieved Result]"
5. **Urgency**: "[Offer] Ends [Timeframe] — [CTA]"

### Copy Length by Platform

- **Google Search**: Maximize character limits. Use all 15 headlines and 4 descriptions in RSAs.
- **Meta Feed**: 125 characters primary text for mobile visibility, but test long-form (3-5 paragraphs) for complex products
- **LinkedIn**: Introductory text under 150 characters for engagement; longer for thought leadership
- **Display**: Minimal text — let the visual do the work. One headline, one CTA.

## Landing Page Alignment

The #1 conversion killer is message mismatch between ad and landing page.

**Alignment checklist:**
- [ ] Headline on landing page matches or mirrors the ad headline
- [ ] The specific offer/CTA mentioned in the ad is immediately visible
- [ ] Visual consistency (colors, imagery style) between ad and page
- [ ] Landing page loads in under 3 seconds on mobile
- [ ] Single CTA — remove navigation, footer links, and competing actions
- [ ] Social proof visible above the fold (logos, testimonials, review count)
- [ ] Form fields minimized (every additional field reduces conversion 5-10%)

## ROAS Optimization Playbook

### Step 1: Fix the Foundation
- Conversion tracking is accurate (check for duplicates, verify with server-side events)
- Attribution window matches your sales cycle
- Exclude irrelevant traffic (negative keywords, placement exclusions, geo exclusions)

### Step 2: Optimize Targeting
- Analyze converting audiences — double down on what works
- Create lookalikes from your best customers, not all customers
- Layer exclusions to prevent wasted spend

### Step 3: Improve Creative
- Test systematically: one variable at a time (headline, image, CTA, offer)
- Kill underperformers at statistical significance (not gut feel)
- Refresh creative every 2-4 weeks to combat fatigue

### Step 4: Optimize Post-Click
- A/B test landing pages (headline, form length, CTA placement)
- Speed optimization (compress images, lazy load, minimize JS)
- Add trust signals (reviews, security badges, money-back guarantees)

### Step 5: Scale
- Increase budgets by 20-30% every 3-5 days (avoid shocking the algorithm)
- Expand to new audiences only after saturating current ones
- Launch on additional platforms using winning creative and messaging

## Retargeting Strategy

### Audience Windows and Messaging

| Window | Audience | Message | Bid Adjustment |
|--------|----------|---------|----------------|
| 1-3 days | Cart abandoners | "You left something behind" + incentive | +50% |
| 1-7 days | Product viewers | Product-specific benefits, reviews | +30% |
| 7-14 days | Site visitors | Category-level value props | +10% |
| 14-30 days | Engaged visitors | Educational content, case studies | Base |
| 30-90 days | Past visitors | Brand awareness, new offers | -20% |
| 90-180 days | Lapsed visitors | Re-introduction, major promos only | -40% |

### Cross-Platform Retargeting

- Use Google Display and YouTube to retarget Meta ad engagers (via site pixel)
- Use Meta to retarget Google Search visitors
- This cross-platform approach reinforces your message and captures different browsing contexts

### Frequency Capping

- Set frequency caps to avoid ad fatigue: 3-5 impressions per user per day for retargeting
- Rotate creative every 2 weeks within retargeting campaigns
- Monitor frequency metrics — when frequency exceeds 8-10 and CTR drops, refresh everything

## Key Metrics and Benchmarks

Track these metrics weekly:

| Metric | What It Tells You | Action Threshold |
|--------|-------------------|------------------|
| CTR | Ad relevance | Below 1% (Search) or 0.5% (Social) = refresh creative |
| CPC | Market competition | Rising 20%+ month-over-month = review targeting |
| CPA | Acquisition efficiency | Above target = optimize targeting and landing page |
| ROAS | Revenue efficiency | Below 3x for e-commerce = audit full funnel |
| Conversion Rate | Landing page effectiveness | Below 2% = landing page issues |
| Quality Score (Google) | Ad relevance + experience | Below 6 = rewrite ads and improve landing page |
| Frequency | Ad fatigue risk | Above 5 = rotate creative |
| Impression Share | Market coverage | Below 70% on brand terms = increase budget |

## Common Mistakes to Avoid

1. **Optimizing for vanity metrics** — Clicks and impressions mean nothing if they don't convert
2. **Too many campaigns** — Fragments data and prevents algorithms from learning
3. **Ignoring search terms report** — You're paying for irrelevant clicks without negative keywords
4. **Identical ads across platforms** — Each platform has different user intent and creative norms
5. **No exclusion strategy** — Always exclude converters, competitors, and irrelevant audiences
6. **Changing too many variables at once** — Makes it impossible to know what worked
7. **Killing campaigns too early** — Allow 2-3x your target CPA in spend before judging performance
8. **Not tracking offline conversions** — Import CRM data back into ad platforms for smarter optimization
