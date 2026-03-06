---
name: schema-markup
description: |
  Implement structured data markup using JSON-LD for enhanced search visibility.
  Covers common schema types, required properties, framework integration, and
  validation. Use when asked to "add schema markup", "implement structured data",
  "add JSON-LD", "set up rich snippets", "add FAQ schema", or "fix schema errors".
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - schema
    - structured-data
    - json-ld
    - rich-snippets
    - seo
---

# Structured Data Implementation

## Why Structured Data Matters

Structured data helps search engines understand the content, context, and
relationships on your pages. It enables rich results in SERPs (star ratings,
FAQ dropdowns, recipe cards, event listings) which increase click-through rates
by 20-30% on average.

Beyond traditional search, structured data is increasingly important for AI
search engines, which use it to extract and cite information with higher
confidence.

## Format: JSON-LD (Recommended)

Google recommends JSON-LD (JavaScript Object Notation for Linked Data) over
Microdata or RDFa. JSON-LD is:

- **Decoupled from HTML** — placed in a `<script>` tag, not interleaved with
  markup, making it easier to maintain.
- **Easier to generate dynamically** — can be injected by JavaScript frameworks
  or CMS plugins.
- **Less error-prone** — no risk of broken nesting or missing closing tags
  affecting the structured data.

Place JSON-LD in the `<head>` of the page (preferred) or anywhere in the
`<body>`. Multiple JSON-LD blocks on a single page are valid.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example Corp"
}
</script>
```

---

## Common Schema Types

### Organization

Use on the homepage or about page to establish your brand entity.

**Required properties:**
- `name` — Legal or commonly known business name.
- `url` — Homepage URL.

**Recommended properties:**
- `logo` — URL to the organization logo (min 112x112px, square or landscape).
- `sameAs` — Array of official social profile URLs (LinkedIn, Twitter, etc.).
- `contactPoint` — Customer service contact with `telephone` and
  `contactType`.
- `description` — Brief description of the organization.
- `foundingDate` — ISO 8601 date.
- `address` — PostalAddress object.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example Corp",
  "url": "https://www.example.com",
  "logo": "https://www.example.com/logo.png",
  "description": "Example Corp provides enterprise analytics solutions.",
  "foundingDate": "2015-03-01",
  "sameAs": [
    "https://www.linkedin.com/company/example-corp",
    "https://twitter.com/examplecorp"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+1-555-123-4567",
    "contactType": "customer service",
    "availableLanguage": ["English"]
  }
}
```

### Article / BlogPosting

Use on blog posts, news articles, and editorial content.

**Required properties:**
- `headline` — Article title (max 110 characters for Google).
- `image` — Representative image (at least one; multiple sizes recommended).
- `datePublished` — ISO 8601 date.
- `author` — Person or Organization object (Google now requires `author.url`
  or `author.name` at minimum).

**Recommended properties:**
- `dateModified` — When the article was last updated.
- `publisher` — Organization with `name` and `logo`.
- `description` — Summary of the article.
- `mainEntityOfPage` — Canonical URL of the page.
- `wordCount` — Integer word count.

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "How to Implement Schema Markup for SEO",
  "image": "https://www.example.com/images/schema-guide.jpg",
  "datePublished": "2025-01-15",
  "dateModified": "2025-06-01",
  "author": {
    "@type": "Person",
    "name": "Jane Smith",
    "url": "https://www.example.com/authors/jane-smith"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Example Corp",
    "logo": {
      "@type": "ImageObject",
      "url": "https://www.example.com/logo.png"
    }
  },
  "description": "A complete guide to implementing JSON-LD structured data for improved search visibility.",
  "mainEntityOfPage": "https://www.example.com/blog/schema-markup-guide"
}
```

### Product

Use on product pages for e-commerce or SaaS product listings.

**Required properties:**
- `name` — Product name.
- `image` — Product image URL.

**Required for rich results:**
- `offers` — Offer object with `price`, `priceCurrency`, and `availability`.
- `review` or `aggregateRating` — At least one for star ratings in SERPs.

**Recommended properties:**
- `description` — Product description.
- `brand` — Brand object with `name`.
- `sku` — Stock keeping unit.
- `gtin` / `gtin13` / `isbn` — Global identifiers.

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Analytics Pro Dashboard",
  "image": "https://www.example.com/images/analytics-pro.jpg",
  "description": "Real-time analytics dashboard for marketing teams.",
  "brand": {
    "@type": "Brand",
    "name": "Example Corp"
  },
  "sku": "AP-2025",
  "offers": {
    "@type": "Offer",
    "price": "99.00",
    "priceCurrency": "USD",
    "availability": "https://schema.org/InStock",
    "url": "https://www.example.com/products/analytics-pro"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.7",
    "reviewCount": "234"
  }
}
```

### FAQPage

Use on pages with question-and-answer content. Generates expandable FAQ rich
results in Google.

**Required properties:**
- `mainEntity` — Array of Question objects, each with `name` (the question)
  and `acceptedAnswer` containing an Answer object with `text`.

**Important rules:**
- The FAQ content must be visible on the page — do not add FAQ schema for
  content that does not appear in the page body.
- Each question-answer pair must be unique across the site.
- Google may limit FAQ rich results to well-known, authoritative sites since
  the August 2023 update.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is JSON-LD?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "JSON-LD (JavaScript Object Notation for Linked Data) is a method of encoding structured data using JSON. It is the recommended format by Google for implementing schema markup on web pages."
      }
    },
    {
      "@type": "Question",
      "name": "Where should I place JSON-LD on my page?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Place JSON-LD in a script tag with type 'application/ld+json' in the head or body of your HTML document. The head section is preferred."
      }
    }
  ]
}
```

### HowTo

Use on instructional content with step-by-step processes.

**Required properties:**
- `name` — Title of the how-to guide.
- `step` — Array of HowToStep objects with `name` and `text`.

**Recommended properties:**
- `totalTime` — ISO 8601 duration (e.g., `PT30M` for 30 minutes).
- `estimatedCost` — MonetaryAmount object.
- `supply` — Materials needed.
- `tool` — Tools needed.
- `image` — Image for each step (recommended for visual rich results).

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to Add Schema Markup to Your Website",
  "totalTime": "PT15M",
  "step": [
    {
      "@type": "HowToStep",
      "name": "Identify the schema type",
      "text": "Determine which schema type matches your page content. Use schema.org to browse available types.",
      "position": 1
    },
    {
      "@type": "HowToStep",
      "name": "Write the JSON-LD",
      "text": "Create a JSON-LD object with the required and recommended properties for your chosen schema type.",
      "position": 2
    },
    {
      "@type": "HowToStep",
      "name": "Add to your page",
      "text": "Insert the JSON-LD in a script tag in the head of your HTML document.",
      "position": 3
    },
    {
      "@type": "HowToStep",
      "name": "Validate",
      "text": "Use Google's Rich Results Test to verify your structured data is error-free.",
      "position": 4
    }
  ]
}
```

### BreadcrumbList

Use on every page to show the navigation path. Generates breadcrumb rich
results in Google.

**Required properties:**
- `itemListElement` — Array of ListItem objects with `position`, `name`, and
  `item` (URL).

The last item in the list (current page) should omit the `item` URL property.

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://www.example.com/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Blog",
      "item": "https://www.example.com/blog/"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "Schema Markup Guide"
    }
  ]
}
```

### LocalBusiness

Use for businesses with physical locations. Generates the local knowledge
panel and map results.

**Required properties:**
- `name` — Business name.
- `address` — PostalAddress object with `streetAddress`, `addressLocality`,
  `addressRegion`, `postalCode`, `addressCountry`.

**Recommended properties:**
- `geo` — GeoCoordinates with `latitude` and `longitude`.
- `telephone` — Phone number.
- `openingHoursSpecification` — Array of opening hours.
- `priceRange` — Price range indicator (e.g., "$$").
- `image` — Business photos.
- `url` — Website URL.

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Example Coffee Shop",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main Street",
    "addressLocality": "Portland",
    "addressRegion": "OR",
    "postalCode": "97201",
    "addressCountry": "US"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 45.5155,
    "longitude": -122.6789
  },
  "telephone": "+1-503-555-0100",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "07:00",
      "closes": "18:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Saturday", "Sunday"],
      "opens": "08:00",
      "closes": "16:00"
    }
  ],
  "priceRange": "$$"
}
```

### SoftwareApplication

Use for software product pages, app listings, and SaaS products.

**Required for rich results:**
- `name` — Application name.
- `offers` — Offer with pricing (use `price: "0"` for free apps).

**Recommended properties:**
- `applicationCategory` — Category (e.g., "BusinessApplication",
  "GameApplication").
- `operatingSystem` — Required OS (e.g., "Windows 10", "iOS 16").
- `aggregateRating` — User ratings.
- `screenshot` — Screenshot URLs.

```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "Analytics Pro",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "offers": {
    "@type": "Offer",
    "price": "99.00",
    "priceCurrency": "USD"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.7",
    "ratingCount": "1250"
  }
}
```

---

## Framework Integration

### Static HTML

Place the JSON-LD script tag directly in the HTML `<head>`:

```html
<head>
  <script type="application/ld+json">
    { "@context": "https://schema.org", ... }
  </script>
</head>
```

### React / Next.js

Use the `<script>` tag with `dangerouslySetInnerHTML` or Next.js's built-in
`<Script>` component:

```jsx
// React component approach
function SchemaMarkup({ schema }) {
  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(schema) }}
    />
  );
}

// Usage
const articleSchema = {
  "@context": "https://schema.org",
  "@type": "Article",
  headline: "My Article Title",
  datePublished: "2025-01-15",
  author: { "@type": "Person", name: "Jane Smith" }
};

export default function Page() {
  return (
    <>
      <SchemaMarkup schema={articleSchema} />
      <article>...</article>
    </>
  );
}
```

For Next.js App Router (13+), use the `metadata` export or place JSON-LD in
the layout/page component:

```jsx
// app/blog/[slug]/page.jsx
export default function BlogPost({ params }) {
  const post = getPost(params.slug);

  const jsonLd = {
    "@context": "https://schema.org",
    "@type": "Article",
    headline: post.title,
    datePublished: post.publishedAt,
    dateModified: post.updatedAt,
    author: {
      "@type": "Person",
      name: post.author.name,
      url: post.author.url
    }
  };

  return (
    <>
      <script
        type="application/ld+json"
        dangerouslySetInnerHTML={{ __html: JSON.stringify(jsonLd) }}
      />
      <article>{/* content */}</article>
    </>
  );
}
```

### Dynamic Generation from CMS Data

When pulling content from a CMS (WordPress, Contentful, Sanity), generate
schema dynamically:

```javascript
function generateArticleSchema(post) {
  return {
    "@context": "https://schema.org",
    "@type": "Article",
    headline: post.title.substring(0, 110),
    image: post.featuredImage?.url,
    datePublished: post.publishedAt,
    dateModified: post.updatedAt || post.publishedAt,
    author: {
      "@type": "Person",
      name: post.author.name,
      url: `https://example.com/authors/${post.author.slug}`
    },
    publisher: {
      "@type": "Organization",
      name: "Example Corp",
      logo: {
        "@type": "ImageObject",
        url: "https://example.com/logo.png"
      }
    },
    description: post.excerpt?.substring(0, 160),
    mainEntityOfPage: `https://example.com/blog/${post.slug}`
  };
}
```

---

## Validation

### Google Rich Results Test

- URL: https://search.google.com/test/rich-results
- Tests whether your page is eligible for rich results.
- Shows both detected structured data items and any errors or warnings.
- Test both the live URL and the rendered HTML (for JavaScript-rendered pages).

### Schema.org Validator

- URL: https://validator.schema.org/
- Validates against the full schema.org specification (not limited to what
  Google supports).
- Useful for checking correctness even for schema types Google does not
  currently use for rich results.

### Google Search Console

- The "Enhancements" section shows structured data issues detected across
  your entire site during regular crawling.
- More reliable than one-off testing because it catches issues at scale.

---

## Common Mistakes

### 1. Schema Does Not Match Visible Content

The structured data must reflect content actually visible on the page. Adding
FAQ schema for questions not on the page, or Product schema with a price that
differs from the displayed price, violates Google's guidelines and can result
in a manual action (penalty).

### 2. Missing Required Properties

Each schema type has required properties for rich result eligibility. A Product
without `offers` will not generate price rich results. An Article without
`author` will not qualify. Always check the requirements at
https://developers.google.com/search/docs/appearance/structured-data.

### 3. Incorrect Nesting

Properties must be nested correctly. A common mistake is placing `author` as
a string instead of a Person object:

```json
// WRONG
"author": "Jane Smith"

// CORRECT
"author": {
  "@type": "Person",
  "name": "Jane Smith"
}
```

### 4. Using Microdata and JSON-LD Together for the Same Entity

Do not mark up the same content with both Microdata (in HTML attributes) and
JSON-LD. This creates duplicate signals that can confuse parsers. Pick one
format per entity.

### 5. Not Updating Schema When Content Changes

Schema markup must stay in sync with page content. If you change a product
price, update the hours of a business, or modify an article, the corresponding
structured data must be updated simultaneously.

### 6. Invalid Date Formats

Dates must be in ISO 8601 format: `YYYY-MM-DD` or `YYYY-MM-DDTHH:MM:SSZ`.
Common mistakes include `MM/DD/YYYY` or written-out dates like "January 15,
2025."

### 7. Exceeding Google's Scope

schema.org defines hundreds of types and properties. Google only supports a
subset for rich results. Implementing unsupported types is not harmful but
will not generate rich results. Focus implementation effort on types Google
actively supports: Article, Product, FAQPage, HowTo, BreadcrumbList,
LocalBusiness, Organization, Event, Recipe, Review, VideoObject, and
SoftwareApplication.
