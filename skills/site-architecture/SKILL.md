---
name: site-architecture
description: |
  Design website information architecture optimized for SEO and user experience.
  Covers URL structure, navigation, topic clusters, internal linking, crawl depth,
  and faceted navigation. Use when asked to "plan site structure", "organize
  website architecture", "design URL hierarchy", "create topic clusters",
  "improve internal linking", or "fix site navigation for SEO".
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - site-architecture
    - information-architecture
    - internal-linking
    - topic-clusters
    - navigation
    - url-structure
---

# Website Information Architecture for SEO

## Why Architecture Matters

Site architecture determines three critical outcomes:

1. **Crawl efficiency** — How effectively search engine bots discover and
   index your pages. Poor architecture means important pages are buried or
   never found.
2. **Link equity distribution** — How authority flows from high-value pages
   (homepage, pages with backlinks) to the pages you want to rank. Authority
   concentrates at the top of the hierarchy and must be deliberately
   distributed.
3. **User experience** — How easily visitors find what they need. Google
   uses engagement signals (bounce rate, pogo-sticking, time on site) as
   indirect ranking factors. Confusing navigation produces poor signals.

A well-designed site architecture makes every page easy to find for both
crawlers and humans, distributes authority effectively, and clearly
communicates topical relevance and relationships.

---

## URL Structure

### Design Principles

URLs should be:

- **Descriptive** — A human should understand the page topic from the URL
  alone.
- **Concise** — Shorter URLs correlate with higher rankings (Backlinko study
  of 11.8M Google results). Aim for under 75 characters.
- **Consistent** — Follow the same pattern across the entire site. Do not
  mix conventions.
- **Lowercase** — URLs are case-sensitive on most servers. Always use
  lowercase to prevent duplicate content issues.
- **Hyphen-separated** — Use hyphens, not underscores. Google treats hyphens
  as word separators but underscores as joiners.

### URL Hierarchy

The URL path should mirror the site's logical hierarchy:

```
https://example.com/
https://example.com/blog/
https://example.com/blog/seo-guide/
https://example.com/products/
https://example.com/products/analytics-dashboard/
https://example.com/products/analytics-dashboard/pricing/
```

**Rules:**

- Maximum 3-4 path segments after the domain. Deeper nesting dilutes keyword
  relevance and makes URLs unwieldy.
- Every directory level should have a corresponding index page. `/blog/`
  should resolve to the blog listing, not a 404.
- Avoid meaningless path segments: `/pages/`, `/content/`, `/site/`, `/en/us/`
  (unless genuinely needed for internationalization).

### Trailing Slash Convention

Pick one convention (with or without trailing slash) and enforce it site-wide
with redirects. Both are valid, but mixing them creates duplicate content.

```
Consistent: /blog/seo-guide/ (all with trailing slash)
Consistent: /blog/seo-guide  (all without trailing slash)
Inconsistent: /blog/ and /blog/seo-guide (mixed — avoid)
```

### Parameter URLs

Query parameters (`?sort=price&color=blue`) should not create indexable pages
unless they represent genuinely unique content. Handle with:

- `robots.txt` disallow for parameter patterns.
- Canonical tags pointing to the clean URL.
- Google Search Console URL parameter configuration (legacy but still
  functional).
- `noindex` on filtered/sorted variations.

---

## Navigation Design

### Primary Navigation

The primary navigation (main menu) serves two purposes:

1. **User wayfinding** — Helps visitors understand what the site offers and
   find key sections.
2. **Crawl path establishment** — Every page linked from the main nav is one
   click from the homepage, receiving maximum link equity.

**Best practices:**

- Limit primary nav to 5-7 top-level items. More than 7 creates cognitive
  overload and dilutes link equity per item.
- Use descriptive, keyword-inclusive labels. "Solutions" is vague;
  "Marketing Analytics" is descriptive.
- Include your highest-priority pages (those you most want to rank) in the
  primary nav or one level below it.
- Avoid JavaScript-only navigation that search engines cannot parse. Use
  semantic HTML (`<nav>`, `<a href>`) with JavaScript enhancement.

### Mega Menus

Mega menus (large dropdown panels) are useful for sites with many categories
but carry SEO risks:

- Every link in a mega menu is a homepage-level link. Linking 200 pages from
  the mega menu means the homepage's link equity is split 200+ ways.
- Ensure mega menu links are crawlable HTML, not dynamically loaded on hover
  via JavaScript.
- Use a clear visual hierarchy within the mega menu — group items by category
  with descriptive headers.

### Footer Navigation

The footer is appropriate for:

- Legal pages (privacy, terms, accessibility).
- Sitemap link.
- Contact information.
- Secondary pages that need to be accessible but are not primary ranking
  targets.

Do not stuff the footer with hundreds of keyword-rich links. Google
devalues footer links relative to in-content and main navigation links.

### Breadcrumbs

Breadcrumbs provide:

- A secondary navigation path showing the user's location in the hierarchy.
- Internal links from deep pages back to category and parent pages.
- Rich result eligibility when marked up with BreadcrumbList schema.

**Implementation:**

```html
<nav aria-label="Breadcrumb">
  <ol>
    <li><a href="/">Home</a></li>
    <li><a href="/blog/">Blog</a></li>
    <li aria-current="page">SEO Guide</li>
  </ol>
</nav>
```

Every page except the homepage should have breadcrumbs. The current page
(last item) should not be a link.

---

## Topic Clusters and the Hub-Spoke Model

### Concept

A topic cluster is a group of related pages organized around a central
"pillar" page (the hub) with supporting "cluster" pages (the spokes) that
cover subtopics in depth.

This structure signals to search engines that your site has comprehensive
coverage of a topic, building topical authority. Sites with strong topic
clusters outrank sites with isolated, unconnected content on the same topics.

### Architecture

```
                    ┌──────────────┐
                    │   Pillar     │
                    │  (Hub Page)  │
                    │  /topic/     │
                    └──────┬───────┘
                           │
          ┌────────────────┼────────────────┐
          │                │                │
    ┌─────┴─────┐   ┌─────┴─────┐   ┌─────┴─────┐
    │  Cluster   │   │  Cluster   │   │  Cluster   │
    │  Page A    │   │  Page B    │   │  Page C    │
    │ /topic/a/  │   │ /topic/b/  │   │ /topic/c/  │
    └───────────┘   └───────────┘   └───────────┘
```

### Pillar Page (Hub)

- Targets the broad, high-volume head keyword (e.g., "content marketing").
- Provides a comprehensive overview of the entire topic (2,000-5,000 words).
- Links to every cluster page in the group with descriptive anchor text.
- Serves as the authoritative entry point for the topic.
- Lives at a high level in the URL hierarchy: `/content-marketing/`.

### Cluster Pages (Spokes)

- Each targets a specific long-tail subtopic (e.g., "content marketing
  strategy for B2B SaaS").
- Provides deep, focused coverage of the subtopic (1,000-3,000 words).
- Links back to the pillar page (reinforcing its authority).
- Links to 2-3 related cluster pages within the same topic cluster.
- Lives one level deeper: `/content-marketing/b2b-saas-strategy/`.

### Planning Topic Clusters

**Step 1: Identify core topics**

List the 5-10 broad topics that represent your business's expertise and
target audience's interests.

**Step 2: Map subtopics**

For each core topic, identify 8-15 subtopics using:
- Keyword research (related keywords, "People Also Ask").
- Competitor content analysis (what subtopics do ranking competitors cover?).
- Customer questions (support tickets, sales calls, community forums).
- Search console data (queries you get impressions for but do not rank well).

**Step 3: Audit existing content**

Map existing pages to the cluster structure. Identify:
- Pages that should become pillar pages (consolidate thin pages if needed).
- Pages that fit as cluster pages.
- Gaps where no content exists for important subtopics.
- Redundant pages targeting the same subtopic (consolidate).

**Step 4: Plan the internal linking**

Document which pages link to which. Every cluster page must link to the
pillar. The pillar must link to every cluster page. Cross-links between
clusters should follow topical relevance.

---

## Internal Linking Strategy

### Link Equity Flow

Link equity (ranking power) flows through internal links. The homepage
receives the most external links and passes equity to pages it links to.
Each subsequent hop dilutes the equity.

```
Homepage (most authority)
  → Category pages (high authority)
    → Subcategory pages (moderate authority)
      → Individual content pages (authority depends on internal links)
```

### Strategic Internal Linking Rules

**1. Link from high-authority pages to priority targets.**

If your homepage has 500 backlinks and your target page has 2, an internal
link from homepage to target is the single most impactful internal link
you can create.

**2. Use descriptive anchor text.**

The anchor text of an internal link tells search engines what the target
page is about. Use the target page's primary keyword or a close variation.

- Good: `<a href="/seo-guide/">complete SEO guide</a>`
- Bad: `<a href="/seo-guide/">click here</a>`
- Bad: `<a href="/seo-guide/">read more</a>`

**3. Link contextually within content.**

Links placed within the body content of a page carry more weight than
navigation links, sidebar links, or footer links. Prioritize in-content
contextual links.

**4. Avoid orphan pages.**

An orphan page has no internal links pointing to it. It can only be
discovered via the sitemap (if included) and receives no link equity.
Audit regularly and fix by adding contextual links from related pages.

**5. Limit links per page.**

There is no hard limit, but each additional link on a page dilutes the
equity passed per link. A page with 10 internal links passes roughly 10x
more equity per link than a page with 100 internal links. Be selective.

### Internal Link Audit Process

1. Crawl the site with Screaming Frog, Sitebulb, or Ahrefs Site Audit.
2. Export the internal link report.
3. Identify:
   - Orphan pages (0 incoming internal links).
   - Deep pages (more than 3 clicks from homepage).
   - Pages with excessive outgoing links (100+).
   - Broken internal links (404 targets).
   - Redirect chains in internal links (update to final destination).
4. Map link equity: which pages have the most incoming internal and
   external links? Are they linking to your priority pages?

---

## Crawl Depth: The 3-Click Rule

Every important page on your site should be reachable within 3 clicks from
the homepage. This is not a hard rule from Google, but empirical data
consistently shows:

- Pages at crawl depth 1-3 are crawled more frequently.
- Pages at crawl depth 4+ are crawled less frequently and may take weeks
  or months to be indexed.
- Pages at crawl depth 6+ are often never indexed on sites without
  extraordinary authority.

### Calculating Crawl Depth

Crawl depth is not the same as URL depth. A page at `/a/b/c/d/e/` (URL
depth 5) can have crawl depth 1 if linked directly from the homepage.

**Tools to measure crawl depth:**
- Screaming Frog: "Crawl Depth" column in the Internal tab.
- Sitebulb: Crawl depth visualization.
- Ahrefs Site Audit: "Depth" report.

### Reducing Crawl Depth

- Add category pages to the main navigation (depth 1).
- Link popular/important content from category pages (depth 2).
- Use "related content" sections on each page to create lateral links.
- Implement HTML sitemaps organized by category for deep content.
- Use pagination wisely — page 50 of a paginated list should not be the
  only path to its content.

---

## Faceted Navigation

Faceted navigation (filters on e-commerce or directory sites) creates SEO
challenges because every combination of filters can generate a unique URL,
potentially creating millions of thin, duplicate, or near-duplicate pages.

### The Problem

A product listing page with 5 filter categories, each with 10 options,
creates 10^5 = 100,000 potential URL combinations. Most of these have
zero search value and waste crawl budget.

### Solutions

**1. Determine which facets have search value.**

Some filter combinations represent real searches:
- "red running shoes size 10" = real search intent = indexable.
- "red running shoes sorted by price ascending" = no search intent = not
  indexable.

**2. Implementation approaches:**

| Facet Type | Has Search Value? | Handling |
|------------|-------------------|----------|
| Category (shoes, boots) | Yes | Separate crawlable URLs |
| Key attributes (color, size, brand) | Often yes | Crawlable URLs with canonicalization |
| Sort order (price, date, rating) | No | AJAX, no URL change, or noindex |
| Pagination (page 2, page 3) | Partially | Crawlable but self-canonical |
| Multi-select combinations | Rarely | Noindex + canonical to broadest filter |

**3. Technical implementation:**

- Use `rel="canonical"` on filtered pages pointing to the unfiltered
  category page (when the filtered page has no unique search value).
- Use `noindex, follow` on low-value filter combinations — the `follow`
  allows crawlers to discover products linked from filtered pages.
- Block highly parameterized URLs in robots.txt as a crawl budget
  protection, but only as a supplement to canonical/noindex handling.
- Use AJAX/JavaScript to apply filters that should not create indexable
  URLs (sort order, display options).

---

## Pagination

### Standard Pagination

For paginated listing pages (blog archives, product categories):

- Each page should be a separate crawlable URL: `/blog/page/2/`,
  `/blog/page/3/`.
- Each paginated page should self-canonicalize (its canonical points to
  itself, not to page 1).
- Use `rel="next"` and `rel="prev"` link elements. Google deprecated
  them in 2019 but Bing and other crawlers still use them.
- Include page numbers in the title tag: "Blog — Page 2 | Brand".
- Ensure pagination is implemented with `<a href>` links, not JavaScript-
  only navigation.

### Infinite Scroll

Infinite scroll (content loads as the user scrolls) is problematic for SEO
because crawlers do not scroll. Solutions:

- Implement "hybrid" pagination: infinite scroll for users with a
  fallback paginated `/page/N/` URL structure that crawlers can follow.
- Use the Intersection Observer API to load content as users scroll, but
  maintain crawlable paginated URLs in the HTML.

### Load More Buttons

"Load More" buttons that append content via AJAX have the same problem as
infinite scroll — crawlers cannot click buttons. Use the same hybrid
approach: crawlable paginated URLs for bots, enhanced UX for users.

---

## Site Hierarchy Planning

### Step-by-Step Process

**1. Content inventory**

List every page on the site (or every page you plan to create). Categorize
each by:
- Content type (product, blog post, landing page, tool, documentation).
- Primary topic/keyword.
- Business priority (revenue-driving, lead-generating, informational).

**2. Category taxonomy**

Group content into a logical taxonomy:

```
Level 0: Homepage
Level 1: Main categories (5-7 maximum)
Level 2: Subcategories (5-10 per category)
Level 3: Individual content pages
```

**3. Keyword-to-page mapping**

Assign one primary keyword to each page. No two pages should target the
same primary keyword (keyword cannibalization). Use a spreadsheet:

| URL | Page Type | Primary Keyword | Monthly Volume | Category |
|-----|-----------|----------------|----------------|----------|
| /seo-guide/ | Pillar | seo guide | 12,000 | SEO |
| /seo-guide/technical-seo/ | Cluster | technical seo | 4,400 | SEO |
| /seo-guide/on-page-seo/ | Cluster | on page seo | 6,600 | SEO |

**4. Internal link map**

Document the linking relationships:
- Which pages link to which (directional).
- What anchor text is used.
- Identify priority pages that need the most internal link equity.

**5. Navigation wireframe**

Design the navigation before building it:
- Primary nav items and their dropdown structure.
- Breadcrumb paths for each page type.
- Footer link structure.
- Sidebar/contextual navigation elements.

### Architecture Validation

Before implementing, validate the architecture against these criteria:

```
[ ] Every important page is within 3 clicks of the homepage
[ ] No keyword cannibalization (1 primary keyword per page)
[ ] Topic clusters are complete (pillar + all planned cluster pages)
[ ] URL structure is consistent and descriptive
[ ] Navigation labels use descriptive, keyword-inclusive terms
[ ] Breadcrumbs reflect the logical hierarchy
[ ] Faceted navigation is handled (canonical/noindex strategy defined)
[ ] Pagination is crawlable
[ ] No orphan pages in the planned structure
[ ] XML sitemap structure mirrors the site hierarchy
```

---

## Common Architecture Mistakes

### 1. Flat Structure with No Hierarchy

Every page linked from the homepage with no category grouping. This fails
to communicate topical relationships to search engines and creates
navigation chaos for users.

### 2. Excessively Deep Hierarchy

Content buried 5-6 levels deep. Pages at this depth receive minimal link
equity and are crawled infrequently. Flatten the structure.

### 3. Orphaned Content Silos

Topic clusters that do not link to each other at all. While each cluster
should be internally cohesive, relevant cross-cluster links help distribute
authority and guide users to related content.

### 4. Duplicate Navigation Paths

The same page reachable through multiple category paths (`/shoes/red/nike/`
and `/nike/shoes/red/`) without canonicalization. This fragments link equity
and creates duplicate content.

### 5. JavaScript-Dependent Navigation

Navigation that requires JavaScript to render links. If the nav fails to
load without JS, crawlers may not discover linked pages. Always use
progressive enhancement: HTML links first, JavaScript enhancement second.
