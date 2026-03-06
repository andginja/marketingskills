---
name: analytics-tracking
description: |
  Set up and configure marketing analytics infrastructure including GA4, Search
  Console, conversion tracking, and privacy compliance. Use when asked to "set up
  analytics", "configure GA4", "track conversions", "implement UTM parameters",
  "create dashboards", "set up Google Search Console", "fix tracking issues",
  or "implement cookie consent".
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - analytics
    - ga4
    - google-analytics
    - search-console
    - tracking
    - conversions
    - gdpr
---

# Marketing Analytics Setup

## Analytics Architecture Overview

A complete marketing analytics setup has four layers:

1. **Collection** — Capturing data from user interactions (GA4, pixel events,
   server-side tracking).
2. **Processing** — Transforming raw data into meaningful structures (data
   layer, event parameters, user properties).
3. **Reporting** — Visualizing data for decision-making (GA4 reports, Looker
   Studio, custom dashboards).
4. **Activation** — Using data to drive actions (audience targeting, automated
   alerts, optimization).

---

## GA4 Configuration

### Account Structure

```
Google Analytics Account (one per company)
  └── GA4 Property (one per product/website)
       ├── Data Stream: Web (your website)
       ├── Data Stream: iOS App (optional)
       └── Data Stream: Android App (optional)
```

One property per distinct product or website. Do not combine unrelated sites
in a single property — it pollutes data and makes analysis unreliable.

### Installation Methods

**Google Tag Manager (recommended):**

GTM provides the most flexibility and does not require code deployments for
tracking changes.

```html
<!-- Google Tag Manager — place in <head> -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-XXXXXXX');</script>

<!-- noscript fallback — place immediately after <body> -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-XXXXXXX"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
```

**gtag.js (simpler, less flexible):**

Direct installation without GTM. Suitable for simple sites.

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Event Model

GA4 uses an event-based model (not sessions/pageviews like Universal
Analytics). Every interaction is an event with parameters.

**Automatically collected events (no setup needed):**
- `page_view` — Fires on every page load.
- `session_start` — First event in a new session.
- `first_visit` — First visit from a new user.
- `user_engagement` — User has the page in focus for 10+ seconds.
- `scroll` — User scrolls past 90% of the page.
- `click` — Outbound link clicks (when enhanced measurement is on).
- `file_download` — Click on links to common file types.

**Enhanced measurement events (toggle in Data Stream settings):**
- `scroll` — 90% scroll depth.
- `outbound_click` — Clicks to external domains.
- `site_search` — On-site search queries.
- `video_engagement` — YouTube embed play, progress, complete.
- `form_interaction` — Form starts and submissions.

**Recommended custom events:**

```javascript
// Lead form submission
gtag('event', 'generate_lead', {
  form_name: 'contact_form',
  form_location: 'homepage_hero',
  lead_type: 'demo_request'
});

// CTA button click
gtag('event', 'cta_click', {
  cta_text: 'Start Free Trial',
  cta_location: 'pricing_page',
  cta_destination: '/signup'
});

// Content engagement
gtag('event', 'content_engagement', {
  content_type: 'blog_post',
  content_title: document.title,
  engagement_type: 'read_complete',  // or 'share', 'bookmark', 'comment'
  word_count: 2500
});

// Signup completion
gtag('event', 'sign_up', {
  method: 'email',         // or 'google', 'github'
  plan_type: 'free_trial'
});

// Purchase
gtag('event', 'purchase', {
  transaction_id: 'T12345',
  value: 99.00,
  currency: 'USD',
  items: [{
    item_id: 'SKU_12345',
    item_name: 'Analytics Pro',
    price: 99.00,
    quantity: 1
  }]
});
```

### Conversions (Key Events)

In GA4, conversions are called "key events." Any event can be marked as a
key event.

**Setup process:**
1. Navigate to Admin → Events.
2. Find the event you want to mark as a conversion.
3. Toggle "Mark as key event."

**Recommended key events for most sites:**
- `generate_lead` — Form submissions, demo requests.
- `sign_up` — Account creation.
- `purchase` — Completed transactions.
- `begin_checkout` — Started checkout (for funnel analysis).
- `add_to_cart` — Product interest signal.

### Audiences

GA4 audiences define user segments for analysis and remarketing.

**Useful audiences to create:**

```
High-Intent Visitors:
- Visited pricing page AND visited 3+ pages in a session
- Trigger: page_view on /pricing/ + session page count >= 3

Engaged Blog Readers:
- Read 3+ blog posts in 30 days
- Trigger: page_view on /blog/* with count >= 3 in 30-day window

Cart Abandoners:
- Added to cart but did not purchase in 7 days
- Trigger: add_to_cart event WITHOUT purchase event within 7 days

Trial Users Not Converting:
- Signed up for trial 10+ days ago, no purchase
- Trigger: sign_up event 10+ days ago WITHOUT purchase event

Return Visitors:
- Visited 3+ times in 30 days without converting
- Trigger: session_start count >= 3 in 30 days WITHOUT key events
```

---

## Google Search Console

### Setup

1. Verify site ownership via DNS TXT record (most reliable method),
   HTML file upload, or Google Analytics / GTM verification.
2. Submit both `https://www.example.com` and `https://example.com`
   properties. Set the preferred version.
3. Submit XML sitemap: Sitemaps → Add a new sitemap → enter URL.

### Key Reports

**Performance report:**
- Track clicks, impressions, CTR, and average position by query, page,
  country, device, and date.
- Filter by search type: web, image, video, news.
- Compare date ranges to identify trends and drops.

**Pages report (Index Coverage):**
- Monitor which pages are indexed, excluded, and why.
- Key statuses to watch:
  - "Crawled — currently not indexed": Google found the page but chose
    not to index it (usually a quality signal).
  - "Discovered — currently not indexed": Google knows about the page but
    has not crawled it yet (crawl budget issue).
  - "Excluded by noindex tag": Verify this is intentional.
  - "Duplicate without user-selected canonical": Google chose a different
    canonical than you specified.

**Core Web Vitals report:**
- Groups URLs by template and shows CWV status (Good, Needs Improvement,
  Poor) for both mobile and desktop.
- Based on real user data (CrUX), not lab data.

**Links report:**
- Internal links: which pages have the most internal links pointing to them.
- External links: which domains link to your site and which pages they link
  to.
- Top linking text: anchor text distribution.

### Search Console API

For automated monitoring, use the Search Console API to pull data into
dashboards or alerting systems:

```python
# Example: Pull top queries for the last 28 days
from googleapiclient.discovery import build

service = build('searchconsole', 'v1', credentials=credentials)

response = service.searchanalytics().query(
    siteUrl='https://www.example.com',
    body={
        'startDate': '2025-01-01',
        'endDate': '2025-01-28',
        'dimensions': ['query'],
        'rowLimit': 100
    }
).execute()

for row in response.get('rows', []):
    query = row['keys'][0]
    clicks = row['clicks']
    impressions = row['impressions']
    ctr = row['ctr']
    position = row['position']
```

---

## UTM Parameters

UTM (Urchin Tracking Module) parameters tag URLs to identify traffic sources
in analytics.

### The 5 UTM Parameters

| Parameter | Required? | Purpose | Example |
|-----------|-----------|---------|---------|
| `utm_source` | Yes | Traffic source | `google`, `newsletter`, `linkedin` |
| `utm_medium` | Yes | Marketing medium | `cpc`, `email`, `social`, `referral` |
| `utm_campaign` | Yes | Campaign name | `spring_sale`, `product_launch_q1` |
| `utm_term` | No | Paid search keyword | `analytics+software` |
| `utm_content` | No | Ad/link variation | `hero_cta`, `sidebar_banner` |

### UTM Naming Conventions

Consistency is critical. UTM values are case-sensitive in GA4.

**Standard conventions:**

```
Sources (lowercase):
  google, facebook, linkedin, twitter, newsletter, partner_name

Mediums (match GA4 default channel grouping expectations):
  cpc        — Paid search
  email      — Email campaigns
  social     — Organic social media
  paid_social — Paid social media
  display    — Display advertising
  referral   — Partner referrals
  affiliate  — Affiliate links
  video      — Video advertising

Campaigns (lowercase, underscores):
  spring_sale_2025
  product_launch_analytics_pro
  weekly_newsletter_2025_01_15
```

### UTM Rules

- Never use UTM parameters on internal links. UTMs override the original
  source, so an internal link with UTMs makes it look like the visit came
  from that "source" rather than the original referrer.
- Always use a URL builder to avoid typos. Google's Campaign URL Builder
  or a team-shared spreadsheet.
- Document all UTM values in a shared reference to prevent inconsistency
  (`facebook` vs `Facebook` vs `fb`).
- Strip UTM parameters from canonical URLs to prevent duplicate content.

---

## Conversion Tracking

### Server-Side vs Client-Side

**Client-side tracking** (JavaScript tags in the browser):
- Easier to implement.
- Blocked by ad blockers (30-40% of users).
- Subject to ITP/ETP cookie restrictions (Safari 7-day, Firefox strict).
- Less reliable for accurate conversion counts.

**Server-side tracking** (events sent from your server to analytics):
- Not blocked by ad blockers.
- Full control over data quality and completeness.
- More complex to implement.
- Required for accurate conversion tracking in 2025+.

**Recommended approach:** Implement both. Use client-side as the primary
tracking layer and server-side as the source of truth for conversion counting
and reporting.

### GA4 Server-Side Setup via GTM Server Container

1. Set up a GTM Server Container (runs on Cloud Run, App Engine, or your
   own infrastructure).
2. Configure a custom domain (e.g., `analytics.example.com`) — first-party
   domain avoids third-party cookie restrictions.
3. Route client-side GTM requests through the server container.
4. The server container forwards events to GA4, Facebook CAPI, Google Ads,
   etc.

### Cross-Domain Tracking

When users move between your domains (e.g., `www.example.com` to
`app.example.com`), configure cross-domain tracking to maintain session
continuity:

1. In GA4: Admin → Data Streams → Configure tag settings → Configure your
   domains.
2. Add all domains that should share the same user session.
3. GA4 appends a `_gl` parameter to cross-domain links to pass the client ID.

---

## Attribution Models

GA4 uses data-driven attribution as the default model. Understanding
attribution models helps interpret conversion reports.

| Model | How It Works | Best For |
|-------|-------------|----------|
| Data-Driven (default) | ML model distributes credit based on observed conversion patterns | Most situations — let the algorithm decide |
| Last Click | 100% credit to the last touchpoint before conversion | Simple reporting, direct response campaigns |
| First Click | 100% credit to the first touchpoint | Understanding which channels drive awareness |
| Linear | Equal credit across all touchpoints | Valuing the full journey equally |
| Position-Based | 40% first, 40% last, 20% split among middle | Valuing both discovery and closing |
| Time Decay | More credit to touchpoints closer to conversion | Longer sales cycles |

**Where to configure:** Admin → Attribution settings → Reporting attribution
model.

**Key insight:** No single attribution model is "correct." Use data-driven
as the default for reporting, but examine first-click attribution to
understand which channels drive new user acquisition vs. which channels
close conversions.

---

## Custom Dashboards

### GA4 Explorations

GA4's Explorations module allows custom analysis beyond standard reports:

- **Funnel exploration**: Visualize conversion funnels with step-by-step
  drop-off rates.
- **Path exploration**: See the paths users take through your site before
  and after key events.
- **Segment overlap**: Compare audience segments to find high-value
  intersections.
- **Cohort exploration**: Track how user cohorts behave over time (retention,
  conversion).

### Looker Studio (Google Data Studio)

For shareable dashboards and blended data sources:

**Recommended marketing dashboard pages:**

1. **Executive Summary**
   - Key metrics: sessions, users, conversions, revenue.
   - Trend charts: 30-day, 90-day, YoY comparison.
   - Conversion rate by channel.

2. **Acquisition**
   - Traffic by source/medium.
   - Campaign performance table (UTM breakdown).
   - New vs returning users by channel.
   - Cost per acquisition by channel (blended with ad platform data).

3. **Engagement**
   - Top pages by pageviews and engagement rate.
   - Average engagement time by content type.
   - Event counts for key interactions.
   - Site search terms.

4. **Conversions**
   - Funnel visualization (visit → engagement → lead → customer).
   - Conversion rate by landing page.
   - Attribution comparison (data-driven vs last click).
   - Revenue by product/plan (e-commerce).

5. **SEO Performance** (blended with Search Console)
   - Organic clicks and impressions trend.
   - Top queries by clicks and average position.
   - Pages with declining impressions (content decay).
   - Core Web Vitals status summary.

---

## Data Layer Implementation

The data layer is a JavaScript object that stores structured data for use
by tag management systems (GTM). It decouples data collection from
presentation.

### Basic Data Layer Setup

```javascript
// Initialize data layer before GTM loads
window.dataLayer = window.dataLayer || [];

// Push page-level data
window.dataLayer.push({
  event: 'page_data_ready',
  page: {
    type: 'blog_post',        // 'homepage', 'product', 'category', 'blog_post'
    title: document.title,
    author: 'Jane Smith',
    category: 'SEO',
    publishDate: '2025-01-15',
    wordCount: 2500
  },
  user: {
    loginStatus: 'logged_in',  // or 'anonymous'
    userType: 'free',          // 'free', 'trial', 'paid'
    userId: 'hashed_user_id'   // Never send PII — hash the ID
  }
});
```

### E-Commerce Data Layer

Follow GA4's recommended e-commerce data layer schema:

```javascript
// Product impression (when product appears in a list)
window.dataLayer.push({
  event: 'view_item_list',
  ecommerce: {
    item_list_id: 'search_results',
    item_list_name: 'Search Results',
    items: [{
      item_id: 'SKU_12345',
      item_name: 'Analytics Pro',
      price: 99.00,
      item_category: 'Software',
      index: 1
    }]
  }
});

// Add to cart
window.dataLayer.push({
  event: 'add_to_cart',
  ecommerce: {
    currency: 'USD',
    value: 99.00,
    items: [{
      item_id: 'SKU_12345',
      item_name: 'Analytics Pro',
      price: 99.00,
      quantity: 1
    }]
  }
});
```

### Data Layer Best Practices

- Push data layer events BEFORE GTM loads when possible (static page data).
- For dynamic interactions, push immediately when the event occurs.
- Never include PII (email, full name, phone) in the data layer.
- Use consistent naming conventions: `snake_case` for all custom properties.
- Document every data layer variable and event in a shared reference.

---

## Privacy Compliance

### GDPR (EU/EEA)

The General Data Protection Regulation requires explicit consent before
setting non-essential cookies or collecting personal data.

**Requirements:**

- **Consent banner**: Must appear before any tracking fires. Must offer
  granular choices (not just "accept all").
- **No pre-checked boxes**: Consent must be affirmative action.
- **Equal prominence**: "Reject all" must be as easy to find as "Accept all."
- **Record consent**: Store proof of when and what the user consented to.
- **Honor withdrawal**: Users must be able to revoke consent as easily as
  they gave it.

### Consent Mode v2 (Google)

Google's Consent Mode allows you to adjust how Google tags behave based on
user consent status:

```javascript
// Default state — set before GTM loads
gtag('consent', 'default', {
  analytics_storage: 'denied',
  ad_storage: 'denied',
  ad_user_data: 'denied',
  ad_personalization: 'denied',
  functionality_storage: 'granted',
  security_storage: 'granted',
  wait_for_update: 500  // milliseconds to wait for CMP
});

// After user grants consent
gtag('consent', 'update', {
  analytics_storage: 'granted',
  ad_storage: 'granted',
  ad_user_data: 'granted',
  ad_personalization: 'granted'
});
```

When consent is denied, GA4 sends cookieless pings that allow for behavioral
modeling (Google estimates the data gap). This provides partial data
coverage while respecting user choice.

### Cookie Consent Platforms (CMPs)

Popular CMPs that integrate with GTM and GA4:

- **Cookiebot** — Auto-scans site for cookies, generates compliant banners.
- **OneTrust** — Enterprise-grade, supports global privacy regulations.
- **Osano** — Simple setup, good for small-to-medium sites.
- **Cookie Information** — Strong EU compliance features.

### Implementation Checklist

```
COLLECTION
[ ] GA4 property created with correct data stream
[ ] GTM container installed on all pages
[ ] Enhanced measurement events enabled
[ ] Custom events defined and firing correctly
[ ] Key events (conversions) marked in GA4
[ ] Audiences created for remarketing and analysis

SEARCH CONSOLE
[ ] Site ownership verified
[ ] Sitemap submitted
[ ] All site versions verified (www, non-www, http, https)

UTM TRACKING
[ ] UTM naming convention documented
[ ] URL builder template created for the team
[ ] No internal links with UTM parameters

CONVERSION TRACKING
[ ] All conversion points tracked (forms, signups, purchases)
[ ] Server-side tracking implemented for critical conversions
[ ] Cross-domain tracking configured (if applicable)

DASHBOARDS
[ ] Executive summary dashboard created
[ ] Acquisition dashboard with channel breakdown
[ ] Conversion funnel visualization
[ ] SEO dashboard with Search Console data

DATA LAYER
[ ] Data layer initialized before GTM
[ ] Page-level data pushed on every page
[ ] User properties set (login status, user type)
[ ] E-commerce events implemented (if applicable)

PRIVACY
[ ] Cookie consent banner implemented
[ ] Consent Mode v2 configured
[ ] No tracking fires before consent
[ ] Privacy policy updated with analytics disclosure
[ ] Data retention settings configured in GA4
[ ] IP anonymization confirmed (GA4 anonymizes by default)
```
