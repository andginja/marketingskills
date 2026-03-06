---
name: seo-audit
description: |
  Perform a comprehensive SEO audit on any website. Evaluates crawlability,
  technical SEO, on-page optimization, content quality, internal linking, and
  mobile-friendliness. Use when asked to "audit SEO", "check site health",
  "review technical SEO", "evaluate search performance", or "find SEO issues".
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - seo
    - audit
    - technical-seo
    - on-page
    - core-web-vitals
---

# Comprehensive SEO Audit

## Audit Priority Framework

Execute the audit in this order. Issues in earlier phases block the effectiveness
of later phases — fixing content means nothing if search engines cannot crawl it.

1. **Crawlability and Indexation** — Can search engines find and index pages?
2. **Technical Foundations** — Does the site meet performance and security baselines?
3. **On-Page Optimization** — Are individual pages properly optimized?
4. **Content Quality** — Does the content serve user intent and demonstrate expertise?
5. **Internal Linking and Authority** — Is link equity distributed effectively?

---

## Phase 1: Crawlability and Indexation

### robots.txt

- Verify `robots.txt` exists at the root domain (`/robots.txt`).
- Confirm it does not accidentally block critical paths (CSS, JS, images needed
  for rendering).
- Check for `Disallow: /` on production — this is a common staging-to-production
  migration oversight.
- Ensure the sitemap URL is declared: `Sitemap: https://example.com/sitemap.xml`.
- Validate that bot-specific directives (Googlebot, Bingbot) do not conflict
  with the general `User-agent: *` rules.

### XML Sitemaps

- Confirm the sitemap is accessible and returns HTTP 200.
- Validate it contains only canonical, indexable URLs (HTTP 200, no noindex).
- Check that the sitemap does not exceed 50,000 URLs or 50MB uncompressed per
  file. Use a sitemap index file for larger sites.
- Verify `<lastmod>` dates are accurate and update when content actually changes
  — do not set them to the current date on every build.
- Cross-reference sitemap URLs against pages discovered by crawling. Pages in
  the sitemap but returning 404 or redirect indicate staleness.

### Canonicalization

- Every indexable page should have a self-referencing `<link rel="canonical">`.
- Check for conflicting signals: a canonical pointing to URL A while an internal
  link points to URL B (trailing slash variants, www vs non-www, HTTP vs HTTPS).
- Ensure canonical tags are in the `<head>`, not the `<body>` — the latter is
  ignored by Google.
- For paginated content, each page should self-canonicalize (do NOT canonical all
  pages to page 1 unless they are truly duplicate).

### Indexation Status

- Use `site:example.com` in Google to estimate indexed page count.
- Compare indexed count to the number of pages in the sitemap. A large gap in
  either direction signals problems:
  - Far fewer indexed than submitted: crawl budget waste, thin content, or
    noindex issues.
  - Far more indexed than submitted: parameter URLs, faceted navigation, or
    session IDs creating infinite crawl paths.
- Check Google Search Console's "Pages" report for specific exclusion reasons.

### HTTP Status and Redirects

- Crawl the site and flag all non-200 responses.
- Identify redirect chains (more than one hop). Flatten chains to a single 301.
- Find soft 404s — pages returning HTTP 200 but displaying "not found" content.
- Check that 301 redirects are used for permanent moves, not 302s.

---

## Phase 2: Technical Foundations

### Core Web Vitals

These are Google's page experience metrics. Targets are based on the 75th
percentile of real user data (CrUX).

| Metric | Target | What It Measures |
|--------|--------|------------------|
| LCP (Largest Contentful Paint) | < 2.5 seconds | Loading performance — when the main content is visible |
| INP (Interaction to Next Paint) | < 200 milliseconds | Responsiveness — delay between user input and visual response |
| CLS (Cumulative Layout Shift) | < 0.1 | Visual stability — unexpected layout movement |

**LCP optimization checklist:**

- Preload the LCP resource (hero image, heading font).
- Serve images in modern formats (WebP, AVIF) with responsive `srcset`.
- Eliminate render-blocking CSS and JS above the fold.
- Use a CDN for static assets.
- Set explicit `width` and `height` on the LCP image to reserve space.

**INP optimization checklist:**

- Break long JavaScript tasks (>50ms) into smaller chunks using `yield()` or
  `requestIdleCallback`.
- Defer non-critical third-party scripts (analytics, chat widgets, ads).
- Minimize main-thread work during user interactions.
- Avoid layout thrashing (reading then writing DOM properties in a loop).

**CLS optimization checklist:**

- Set explicit dimensions on all images, videos, and iframes.
- Reserve space for ad slots and dynamically injected content.
- Avoid inserting content above existing content (banners, cookie notices that
  push the page down).
- Use `font-display: swap` with size-adjusted fallback fonts to minimize
  font-swap layout shift.

### HTTPS and Security

- The entire site must be served over HTTPS. No mixed content warnings.
- HSTS header should be present: `Strict-Transport-Security: max-age=31536000`.
- Check for valid SSL certificate (not expired, covers all subdomains in use).

### Mobile-Friendliness

- Google uses mobile-first indexing — the mobile version of the page is what
  gets indexed and ranked.
- Verify the viewport meta tag: `<meta name="viewport" content="width=device-width, initial-scale=1">`.
- Test tap targets: interactive elements should be at least 48x48 CSS pixels
  with adequate spacing.
- Ensure no horizontal scrolling is required on mobile viewports.
- Check that content is not hidden behind tabs, accordions, or "read more"
  toggles that might not get indexed (Google generally indexes hidden content
  but deprioritizes it).

### Page Speed

- Run Lighthouse (lab data) and cross-reference with CrUX (field data).
- Check Time to First Byte (TTFB) — should be under 800ms. Slow TTFB indicates
  server-side issues (slow database queries, no caching, distant origin).
- Audit third-party script impact: tag managers, analytics, chat widgets, and
  social embeds are the most common performance killers.
- Verify images are lazy-loaded below the fold but NOT lazy-loaded above the
  fold (the LCP image must load eagerly).

### Structured Data

- Validate all structured data with Google's Rich Results Test.
- Check for warnings (not just errors) — warnings indicate missed opportunities
  for enhanced SERP features.
- Common types to implement: Organization, BreadcrumbList, Article, FAQPage,
  Product, LocalBusiness.

---

## Phase 3: On-Page Optimization

### Title Tags

- Length: 50-60 characters (Google truncates at ~580px display width).
- Include the primary keyword naturally, preferably near the beginning.
- Each page must have a unique title tag. Duplicate titles signal duplicate or
  thin content.
- Format suggestion: `Primary Keyword — Secondary Keyword | Brand`
- Avoid keyword stuffing. One primary keyword and one secondary is sufficient.

### Meta Descriptions

- Length: 150-160 characters.
- Include a clear value proposition and call to action.
- While meta descriptions are not a ranking factor, they directly affect CTR
  from search results.
- Google rewrites meta descriptions ~70% of the time — write them anyway, as
  they influence the rewrite and serve as a fallback.

### Heading Hierarchy

- Every page should have exactly one `<h1>` tag containing the primary keyword.
- Headings should follow a logical hierarchy: H1 → H2 → H3. Do not skip levels
  (e.g., H1 → H3).
- Use headings to outline the content structure, not for visual styling.
- Subheadings (H2, H3) are opportunities for long-tail and related keywords.

### Image Optimization

- All images must have descriptive `alt` text that serves accessibility first
  and SEO second.
- Use descriptive file names (`blue-running-shoes.webp`, not `IMG_4392.webp`).
- Serve images in next-gen formats (WebP, AVIF) with fallbacks.
- Compress images: aim for quality 75-85 in lossy compression.
- Implement responsive images with `srcset` and `sizes` attributes.

### URL Structure

- URLs should be short, descriptive, lowercase, and hyphen-separated.
- Include the primary keyword when natural.
- Avoid parameters, session IDs, and unnecessary nesting.
- Bad: `/p?id=4392&cat=shoes`
- Good: `/running-shoes/blue-nike-pegasus`

---

## Phase 4: Content Quality

### Search Intent Alignment

- For each target keyword, check the current SERP. What type of content ranks?
  - Informational: blog posts, guides, how-tos.
  - Commercial: comparison pages, reviews, "best of" lists.
  - Transactional: product pages, pricing pages.
  - Navigational: brand or product name queries.
- Misaligned intent is the most common reason good content fails to rank.

### Content Depth and E-E-A-T

- Content should demonstrate Experience, Expertise, Authoritativeness, and
  Trustworthiness.
- Include author bios with relevant credentials.
- Cite authoritative sources with outbound links.
- Cover the topic comprehensively — check "People Also Ask" and related searches
  for subtopics to address.
- Update content regularly with accurate, current information.

### Thin Content and Cannibalization

- Identify pages with very little unique content (under 300 words with no other
  value like tools or data).
- Find keyword cannibalization: multiple pages targeting the same keyword,
  splitting ranking signals. Consolidate or differentiate.
- Check for doorway pages — near-identical pages targeting geographic or minor
  keyword variations with no unique value.

---

## Phase 5: Internal Linking and Authority

### Internal Link Audit

- Every important page should be reachable within 3 clicks from the homepage.
- Identify orphan pages (pages with no internal links pointing to them).
- Use descriptive anchor text — not "click here" or "learn more."
- Distribute internal links strategically: link from high-authority pages to
  pages you want to rank.

### Link Equity Distribution

- Check the site's link profile for pages with the most external backlinks.
- Ensure those high-authority pages link internally to priority content.
- Avoid concentrating all internal links on the homepage and top-level
  navigation pages while starving deep content.

### External Link Profile (Overview)

- Review the backlink profile for toxic or spammy links.
- Check referring domain diversity — a healthy profile has links from many
  domains, not many links from few domains.
- Identify lost backlinks to high-value pages and consider reclamation outreach.

---

## Audit Checklist

Use this checklist to ensure completeness. Mark each item as Pass, Fail, or N/A.

```
CRAWLABILITY AND INDEXATION
[ ] robots.txt exists and is correctly configured
[ ] XML sitemap is valid, submitted, and contains only indexable URLs
[ ] All indexable pages have self-referencing canonicals
[ ] No redirect chains (max 1 hop)
[ ] No soft 404s
[ ] Indexed page count approximately matches intended indexable pages

TECHNICAL FOUNDATIONS
[ ] LCP < 2.5s on mobile (75th percentile field data)
[ ] INP < 200ms on mobile (75th percentile field data)
[ ] CLS < 0.1 on mobile (75th percentile field data)
[ ] HTTPS everywhere, no mixed content
[ ] Valid SSL certificate
[ ] Mobile viewport meta tag present
[ ] Tap targets adequately sized (48x48px minimum)
[ ] TTFB < 800ms
[ ] Structured data valid (no errors)

ON-PAGE OPTIMIZATION
[ ] Every page has a unique title tag (50-60 characters)
[ ] Every page has a unique meta description (150-160 characters)
[ ] Every page has exactly one H1
[ ] Heading hierarchy is logical (no skipped levels)
[ ] All images have descriptive alt text
[ ] Images served in modern formats and compressed
[ ] URLs are clean, descriptive, and lowercase

CONTENT QUALITY
[ ] Content aligns with search intent for target keywords
[ ] No thin content pages (< 300 words with no other value)
[ ] No keyword cannibalization between pages
[ ] Author bios and credentials present (YMYL topics)
[ ] Content is current and regularly updated

INTERNAL LINKING AND AUTHORITY
[ ] All important pages reachable within 3 clicks
[ ] No orphan pages
[ ] Descriptive anchor text used (not "click here")
[ ] High-authority pages link to priority content
[ ] External backlink profile reviewed for toxic links
```

---

## Reporting Findings

When presenting audit results, organize findings by:

1. **Critical** — Issues blocking indexation or causing significant ranking loss
   (broken canonicals, noindex on important pages, site-wide 5xx errors).
2. **High** — Issues significantly impacting performance or rankings (failed
   Core Web Vitals, missing title tags, redirect chains).
3. **Medium** — Optimization opportunities that improve competitiveness (thin
   content, missing structured data, suboptimal internal linking).
4. **Low** — Nice-to-haves and minor improvements (image alt text gaps, meta
   description length, URL cleanup).

For each finding, include:
- What the issue is (with specific URLs).
- Why it matters (impact on crawling, ranking, or user experience).
- How to fix it (actionable recommendation with priority).
- Estimated effort (quick win, moderate, or significant development work).
