---
name: programmatic-seo
description: |
  Generate large-scale content pages using templates and data sources for SEO.
  Covers opportunity identification, data pipelines, template design, URL
  structure, and thin content avoidance. Use when asked to "create pages at
  scale", "programmatic SEO", "pSEO strategy", "template-based content",
  "directory SEO", "comparison page generator", or "build landing pages from
  data".
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - programmatic-seo
    - pseo
    - content-at-scale
    - templates
    - data-driven-seo
---

# Programmatic SEO

## What Programmatic SEO Is

Programmatic SEO (pSEO) is the strategy of generating large numbers of search-
optimized pages using structured data, templates, and automation rather than
manually writing each page. Instead of creating 50 pages by hand, you build
one template and populate it with 50 (or 50,000) rows of data.

**Successful examples:**

- Zapier's "How to integrate X with Y" pages (25,000+ pages)
- Nomad List's city pages for remote workers
- Wise's currency conversion pages ("USD to EUR", "GBP to JPY")
- Tripadvisor's location + activity pages
- G2's software comparison pages ("X vs Y")

The approach works when there is a large matrix of queries following a
repeatable pattern, sufficient data to make each page genuinely useful, and
enough search volume across the long tail to justify the investment.

---

## Identifying pSEO Opportunities

### Step 1: Find Repeatable Query Patterns

Look for keyword patterns with a consistent modifier structure:

| Pattern | Example Queries |
|---------|----------------|
| [Tool A] vs [Tool B] | "Notion vs Airtable", "Slack vs Teams" |
| [Service] in [City] | "plumber in Austin", "coworking in Berlin" |
| [Metric] for [Industry] | "average conversion rate for SaaS" |
| [Template] for [Use Case] | "invoice template for freelancers" |
| How to [Action] with [Tool] | "how to create a pivot table with Excel" |
| [Product] alternatives | "Mailchimp alternatives", "Figma alternatives" |
| [Product] pricing | "HubSpot pricing", "Ahrefs pricing" |

### Step 2: Validate Search Volume

A single page in a pSEO set may only get 10-50 searches per month. That is
fine — the value is in aggregate.

**Validation process:**
1. Sample 20-30 queries from your potential matrix.
2. Check search volume for each using Ahrefs, Semrush, or Google Keyword
   Planner.
3. Calculate the total addressable search volume: average volume per query
   multiplied by the number of possible pages.
4. Check the SERP for sampled queries — if results are dominated by
   high-authority sites with manually created content, the bar is higher.

### Step 3: Assess Data Availability

You need structured data that is:

- **Complete** — Gaps in data create thin pages. If 30% of your rows are
  missing key fields, those pages will be low quality.
- **Accurate** — Inaccurate data (wrong prices, outdated stats) damages
  trust and triggers negative user signals.
- **Differentiable** — Each data row must produce a meaningfully different
  page. If 500 pages all say essentially the same thing with minor word
  swaps, Google will treat them as thin/duplicate content.
- **Updatable** — Stale data pages lose value over time. Plan for data
  refresh cycles.

### Step 4: Check Competitive Landscape

Evaluate who currently ranks for your target queries:

- **User-generated content sites** (Reddit, Quora, forums) ranking = strong
  opportunity. Google is serving UGC because no dedicated page exists.
- **Aggregator sites** (Yelp, G2, Capterra) ranking = moderate opportunity.
  You can win with more specialized, deeper content.
- **Established authority sites** with manual content = harder opportunity.
  Your template must produce meaningfully better pages.

---

## Data Sources

### First-Party Data

The strongest pSEO is built on proprietary data that competitors cannot
replicate:

- Product usage analytics (anonymized and aggregated).
- Customer survey data.
- Internal benchmarks and performance data.
- Expert-curated databases.
- Transaction and pricing data.

### Third-Party Data Sources

- **Public APIs**: Government data (census, weather, economic), Wikipedia/
  Wikidata, OpenStreetMap.
- **Commercial APIs**: Crunchbase, Clearbit, Google Maps, industry-specific
  data providers.
- **Web scraping** (where legally permitted): Public product listings,
  published pricing pages, public directories.
- **Aggregated datasets**: Kaggle, Data.gov, World Bank Open Data.

### User-Generated Data

- Reviews and ratings.
- Community-contributed information.
- Forum discussions and Q&A.

---

## Template Design

### Core Template Structure

Every pSEO page needs these elements to avoid being classified as thin content:

```
URL: /[category]/[entity-slug]

<head>
  <title>[Dynamic Title — 50-60 chars]</title>
  <meta name="description" content="[Dynamic description — 150-160 chars]">
  <link rel="canonical" href="[self-referencing canonical]">
  [JSON-LD structured data]
</head>

<body>
  <nav>[Breadcrumbs: Home > Category > Entity]</nav>

  <h1>[Primary heading with entity name]</h1>

  [Hero section: key data points, summary, or primary value proposition]

  <h2>[Data-driven section 1]</h2>
  [Unique content derived from entity-specific data]

  <h2>[Data-driven section 2]</h2>
  [Comparative data, charts, tables]

  <h2>[Contextual content section]</h2>
  [Related information that varies meaningfully per entity]

  <h2>[FAQ section]</h2>
  [Entity-specific questions and answers]

  [Internal links: related entities, parent category, sibling pages]
</body>
```

### Dynamic Meta Tags

Generate meta tags programmatically with entity-specific information:

```javascript
// Title tag generation
function generateTitle(entity) {
  const templates = {
    comparison: `${entity.toolA} vs ${entity.toolB}: Features, Pricing & Verdict (${currentYear})`,
    location: `Best ${entity.service} in ${entity.city} — Top ${entity.count} Rated`,
    tool: `${entity.name} — ${entity.tagline} | Free Online Tool`,
    pricing: `${entity.product} Pricing ${currentYear}: Plans, Costs & Best Value`
  };
  // Truncate to 60 characters
  return templates[entity.type].substring(0, 60);
}

// Meta description generation
function generateDescription(entity) {
  const templates = {
    comparison: `Compare ${entity.toolA} and ${entity.toolB} side by side. See pricing, features, integrations, and user ratings to find the best fit for your needs.`,
    location: `Find the top-rated ${entity.service} providers in ${entity.city}. Compare ${entity.count} verified professionals with reviews, pricing, and availability.`
  };
  return templates[entity.type].substring(0, 160);
}
```

### Avoiding Thin Content

The single biggest risk of pSEO is creating thousands of pages that Google
considers thin, duplicate, or low-value. Mitigation strategies:

**1. Unique data per page**

Every page must contain data that is genuinely different from every other page
in the set. If you remove the entity name and the remaining content is
identical, the page is thin.

**2. Conditional content blocks**

Show or hide template sections based on data availability. An empty section
with a heading and no content is worse than no section at all.

```javascript
// Only render the pricing section if pricing data exists
if (entity.pricing && entity.pricing.length > 0) {
  renderPricingTable(entity.pricing);
}
```

**3. Computed insights**

Transform raw data into insights that add value:

- Instead of just showing "Price: $99/mo", compute "23% cheaper than the
  category average of $129/mo."
- Instead of just listing features, compute a feature coverage score:
  "Covers 8 of 10 essential features for small businesses."
- Generate contextual recommendations based on data patterns.

**4. Minimum quality threshold**

Set a minimum data completeness threshold. If an entity has fewer than N
populated fields, do not generate the page. A noindexed incomplete page is
better than an indexed thin one.

**5. Unique introductory copy**

Invest in writing (or generating with careful review) unique introductory
paragraphs for at least the top 20% of pages by search volume. Use templated
copy with meaningful variable substitution for the remaining 80%.

---

## URL Structure

### URL Pattern Design

Choose a URL structure that is:

- **Predictable** — Users and search engines can infer the URL from the
  content.
- **Flat** — Avoid excessive nesting. `/tools/comparison/slack-vs-teams` is
  fine. `/category/subcategory/type/comparison/slack-vs-teams` is too deep.
- **Keyword-inclusive** — Include the primary keyword naturally.

**Good patterns:**

```
/compare/[tool-a]-vs-[tool-b]
/[city]/[service]
/tools/[tool-name]
/[category]/[entity-slug]
/templates/[use-case]-template
```

**Bad patterns:**

```
/page?id=4392               # No keywords, not human-readable
/data/v2/entity/12345       # API-like, no SEO value
/tools/tool?name=slack      # Query parameters instead of path segments
```

### Handling Edge Cases

- **Bidirectional comparisons**: "Slack vs Teams" and "Teams vs Slack" should
  resolve to a single canonical page. Pick an alphabetical order convention
  or canonicalize one to the other.
- **Special characters in entity names**: Sanitize slugs. "C++" becomes
  "cpp" or "c-plus-plus", not "c++".
- **Duplicate entities**: "New York" and "New York City" must resolve to one
  page, not two.

---

## Internal Linking at Scale

Internal linking is critical for pSEO because search engines must discover
and understand the relationships between potentially thousands of pages.

### Hub-and-Spoke Model

```
Category Hub (/compare)
  ├── /compare/slack-vs-teams
  ├── /compare/slack-vs-discord
  ├── /compare/teams-vs-discord
  └── ...
```

Every entity page links back to its category hub. The hub page links to all
(or the most important) entity pages.

### Cross-Linking Between Entities

On the "Slack vs Teams" page, link to:
- Other comparisons involving Slack: "Slack vs Discord", "Slack vs Zoom"
- Other comparisons involving Teams: "Teams vs Zoom", "Teams vs Google Meet"
- Individual tool pages: "/tools/slack", "/tools/teams"

**Implementation:**

```javascript
function getRelatedPages(entity) {
  // Find pages sharing at least one entity with the current page
  return allPages
    .filter(page => page.entities.some(e => entity.entities.includes(e)))
    .filter(page => page.slug !== entity.slug)
    .slice(0, 8); // Limit to 8 related links
}
```

### Pagination for Large Category Pages

If a category hub has thousands of child pages, paginate with:
- `rel="next"` and `rel="prev"` link elements (still used by some crawlers).
- A clear numbered pagination UI (not infinite scroll for SEO pages).
- Self-referencing canonicals on each paginated page (do NOT canonical
  all pages to page 1).

### XML Sitemap Strategy

For large pSEO sites:
- Use sitemap index files pointing to segmented sitemaps.
- Group sitemaps by category: `sitemap-comparisons.xml`,
  `sitemap-locations.xml`.
- Set accurate `<lastmod>` dates — update when data changes.
- Prioritize new and recently updated pages for faster crawling.

---

## Common pSEO Page Types

### Comparison Pages ("X vs Y")

**Data needed:** Features, pricing, ratings, pros/cons for each entity.
**Template sections:** Side-by-side feature table, pricing comparison, user
ratings summary, verdict/recommendation, related comparisons.
**Key success factor:** Genuine analysis, not just raw data. Include a
recommendation and explain the reasoning.

### Directory Listings

**Data needed:** Business name, location, category, description, contact
info, ratings.
**Template sections:** Search/filter interface, listing cards with key info,
map integration, category navigation.
**Key success factor:** Data freshness and completeness. Stale directories
with incorrect phone numbers or closed businesses lose authority fast.

### Tool / Calculator Pages

**Data needed:** Formulas, input parameters, result formatting rules.
**Template sections:** Input form, calculated results, explanation of
methodology, related tools.
**Key success factor:** The tool must actually work and provide accurate
results. This is pSEO where the "content" is the interactive functionality.

### Location Pages

**Data needed:** Geographic data, local statistics, business/service info
specific to each location.
**Template sections:** Location overview with local data, service details
specific to the area, local testimonials or case studies, map, contact info.
**Key success factor:** Truly local content. Pages that just swap the city
name and keep everything else identical are doorway pages and violate
Google's guidelines.

### Alternatives Pages ("[Product] Alternatives")

**Data needed:** Competitor products with features, pricing, differentiators.
**Template sections:** Why users seek alternatives (common pain points),
top alternatives with brief reviews, comparison table, recommendation by
use case.
**Key success factor:** Objectivity and completeness. Include your product
if relevant but do not make the page a thinly disguised sales pitch.

---

## Quality Control

### Pre-Launch Checklist

```
[ ] Sample 20 pages across different data segments — are they meaningfully
    different from each other?
[ ] Test pages with minimum data — do they still provide value or are they
    obviously thin?
[ ] Verify all dynamic meta tags generate correctly (no truncation issues,
    no missing variables)
[ ] Validate structured data on sample pages
[ ] Check internal links — are related pages correctly linked?
[ ] Test page load speed — data-heavy pages with tables and charts must
    still meet Core Web Vitals
[ ] Review URL structure for edge cases (special characters, long names,
    duplicates)
[ ] Confirm sitemap includes all generated pages
[ ] Set up noindex rules for pages below quality threshold
```

### Post-Launch Monitoring

- **Index coverage**: Track how many pages Google indexes vs. how many you
  generated. Low indexation rate signals quality issues.
- **Crawl budget**: Monitor crawl stats in Search Console. If Google is
  crawling thousands of pSEO pages but not indexing them, reduce the set.
- **Traffic per page**: If the median pSEO page gets 0 organic visits after
  3 months, reevaluate the strategy.
- **User signals**: Monitor bounce rate, time on page, and pogo-sticking
  for pSEO pages vs. manually created pages.
- **Thin content warnings**: Watch for "Crawled — currently not indexed" or
  "Discovered — currently not indexed" status in Search Console.

### Iterative Improvement

pSEO is not "launch and forget." Plan for:

1. **Data refresh cycles** — How often does the underlying data change?
   Set up automated data pipelines with freshness checks.
2. **Template iteration** — Improve templates based on which sections
   users engage with and which pages rank best.
3. **Pruning** — Remove or noindex pages that consistently get no traffic
   and no impressions after 6 months. They waste crawl budget.
4. **Expansion** — Once a template works, identify adjacent query patterns
   to expand into.
