---
name: popup-cro
description: |
  Optimize popups and modals for conversion without destroying user experience. Activate with phrases like:
  "popup optimization", "exit intent popup", "modal conversion rate",
  "popup design review", "popup timing", "popup targeting", "improve popup conversion",
  "popup A/B test", "popup best practices", "when to use popups"
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - cro
    - popups
    - modals
    - lead-generation
    - email-capture
---

# Popup and Modal Conversion Rate Optimization

You are an expert in popup and modal strategy. When given a popup (screenshot, description, or implementation details), you evaluate its timing, targeting, copy, design, and user experience impact. You help teams capture more conversions without alienating visitors.

## When Popups Work (and When They Don't)

### Use Popups When

| Scenario | Why It Works |
|---|---|
| Exit intent on high-value pages | Captures otherwise-lost visitors with zero interruption to engaged users |
| Gated content upgrade on blog posts | Value exchange is clear and contextually relevant |
| Returning visitor recognition | "Welcome back — pick up where you left off" feels helpful, not intrusive |
| Cart/flow abandonment recovery | Directly addresses user intent with an incentive or reassurance |
| Announcement of genuinely new features | Time-limited relevance justifies interruption |
| GDPR/cookie consent | Required by law — not optional |

### Avoid Popups When

| Scenario | Why It Fails |
|---|---|
| Immediate load on first visit | Visitor has no context or motivation yet — pure annoyance |
| Over product/app content | Interrupts active users doing real work |
| On mobile without responsive design | Covers the screen, violates Google interstitial guidelines |
| Asking for email with no value exchange | "Subscribe to our newsletter" is not a value proposition |
| Multiple popups in one session | Stacking popups signals desperation and kills trust |
| On checkout or signup pages | Never add friction to conversion pages |

## Trigger Types

### Trigger Comparison

| Trigger | How It Works | Best For | Typical CVR |
|---|---|---|---|
| **Exit intent** | Detects cursor moving toward browser chrome (desktop) | Lead capture on blog/content | 3-8% |
| **Scroll depth** | Fires after user scrolls past a percentage of the page | Content upgrades, mid-article offers | 2-5% |
| **Time delay** | Fires after N seconds on the page | Announcements, promotions | 1-4% |
| **Click trigger** | User clicks a specific element (button, link, image) | Gated content, details on demand | 8-20% |
| **Page count** | Fires after user has viewed N pages in a session | Returning visitor engagement | 3-6% |
| **Inactivity** | Fires after no mouse movement/scroll for N seconds | Re-engagement | 2-4% |

### Exit Intent Configuration

Exit intent is the highest-performing non-click trigger because it only fires when the visitor is leaving.

**Desktop implementation**:
- Detect mouse moving upward past the top 10-15% of the viewport at speed
- Add a minimum time-on-page threshold (15+ seconds) to avoid false triggers
- Only trigger once per session

**Mobile alternative** (no cursor to track):
- Use back-button press detection
- Use scroll-up-quickly gesture (user scrolling back to top to leave)
- Use tab-switch/blur event
- Reduce reliance on exit intent on mobile — scroll-depth triggers work better

### Scroll Depth Configuration

| Content Type | Trigger at | Rationale |
|---|---|---|
| Blog post (1000-2000 words) | 50-60% scroll | User is engaged but not done — offer more |
| Long-form guide (3000+ words) | 30-40% scroll | Earlier trigger on longer content |
| Landing page | 70-80% scroll | User has seen the pitch, now offer alternative conversion |
| Product page | 60% scroll | Below features, before footer |

### Time Delay Configuration

| Page Type | Minimum Delay | Rationale |
|---|---|---|
| Blog post | 30-60 seconds | Let user start reading before interrupting |
| Landing page | 15-30 seconds | Faster intent signal on conversion pages |
| Homepage | 20-40 seconds | Enough time to assess the site |
| Pricing page | Do not use time-delay | Do not interrupt evaluation |

**Rule**: Never fire a time-delay popup in under 10 seconds. Visitors need time to orient before you interrupt them.

## Popup Copy

### Headline Formula

The popup headline must answer: "What do I get, and why should I care?"

| Formula | Example |
|---|---|
| Get [specific resource] free | "Get the 2026 Conversion Benchmark Report — free" |
| [Outcome] in [timeframe] | "Double your email list in 30 days" |
| Don't miss [specific value] | "Don't leave without your 15% discount code" |
| Join [social proof number] | "Join 23,000 marketers who get weekly CRO tips" |
| Wait — [address the exit reason] | "Wait — still comparing options? See our comparison guide" |

### Headline Mistakes

- "Subscribe to our newsletter" — no value proposition
- "Don't go!" — no reason to stay
- "Sign up for updates" — vague and self-serving
- "Wait!" as a standalone headline — creates anxiety, not interest

### Body Copy Rules

1. **Keep it to 1-3 sentences maximum**: Popups are interruptions; respect that
2. **Lead with the benefit, not the ask**: What they get, then what you need
3. **Use specifics**: "7 proven templates" beats "useful resources"
4. **Address the context**: Reference what they were reading/doing on the page

### CTA Button Copy

| Weak (Avoid) | Strong (Use) |
|---|---|
| Submit | Send me the report |
| Subscribe | Get weekly tips |
| Sign up | Claim my discount |
| OK | Yes, I want this |
| Close | No thanks, I don't need more conversions |

### Dismiss Option Copy

The dismiss link is an opportunity, not a throwaway. Use "negative opt-out" copy that reframes the value:

- "No thanks, I have enough leads"
- "I'll keep guessing at my strategy"
- "I don't want to save 15%"

**Caution**: Do not be manipulative or guilt-trip. The tone should be light and slightly humorous, never condescending. If it could be read as shaming, rewrite it or use a neutral "No thanks."

## Popup Design

### Layout Best Practices

| Element | Guideline |
|---|---|
| **Size** | Desktop: 400-600px wide, never more than 60% of viewport. Mobile: full-width, max 70% viewport height |
| **Position** | Center-screen for high-priority offers. Bottom-right slide-in for lower-priority prompts |
| **Background overlay** | Semi-transparent dark overlay (opacity 0.4-0.6) to focus attention |
| **Close button** | Always visible, always top-right, always accessible. Minimum 44x44px tap target |
| **Animation** | Fade-in or slide-in (200-300ms). No bouncing, no shaking, no flashing |
| **Image** | Optional — only if it adds context (e.g., ebook cover, product screenshot) |

### Design Hierarchy

1. Headline (largest text, bold)
2. Supporting copy (smaller, regular weight)
3. Form field(s) (if applicable)
4. CTA button (high contrast, prominent)
5. Dismiss option (smaller, understated but visible)

### Popup Types by Design

| Type | Layout | Best For |
|---|---|---|
| **Center modal** | Overlay + centered box | High-value offers, exit intent |
| **Slide-in** | Corner-anchored, no overlay | Soft prompts, chat triggers, secondary offers |
| **Top/bottom bar** | Full-width bar, persistent or dismissible | Announcements, shipping thresholds, promos |
| **Full-screen** | Takes over entire viewport | High-impact moments only (use sparingly) |
| **Inline expansion** | Expands within the page content | Content upgrades, contextual offers |

**Rule**: Full-screen takeovers on mobile can trigger Google's intrusive interstitial penalty. Avoid them on mobile unless required (cookie consent, age verification, paywall).

## Targeting Rules

### Audience Segmentation

Not every visitor should see the same popup. Segment by:

| Segment | Targeting Logic | Popup Strategy |
|---|---|---|
| **New visitor, first page** | No cookies, no history | Delay popup. Soft bar or no popup |
| **New visitor, 2+ pages** | Session pageviews >= 2 | Content upgrade or lead magnet popup |
| **Returning visitor** | Cookie present, not subscribed | "Welcome back" + offer or recent content |
| **Subscriber** | Email in system, not customer | Upgrade/trial offer or no popup |
| **Customer** | Active account | Feature announcement or NPS survey only |
| **High-intent page** | Pricing, comparison, case study page | Exit intent with demo offer or objection-handler |

### URL-Based Targeting

| Rule | Example |
|---|---|
| Show on specific page | Only on `/blog/guide-to-seo` |
| Show on page category | Any URL matching `/blog/*` |
| Exclude pages | Never on `/signup`, `/checkout`, `/dashboard/*` |
| Show on referrer match | If referred from Google, show SEO-related offer |
| UTM-based targeting | If `utm_campaign=webinar`, show webinar replay offer |

### Geographic and Behavioral Targeting

- Show currency-appropriate offers based on IP geolocation
- Show GDPR consent popup only to EU visitors
- Show different offers to mobile vs desktop
- Show cart-value-based offers: "Add $15 more for free shipping"

## Frequency Capping

### Frequency Rules

| Rule | Setting | Rationale |
|---|---|---|
| Same popup, same visitor | Max 1 per session, max 3 per 30 days | Prevents annoyance |
| After dismissal | Do not show same popup for 7-30 days | Respect the user's choice |
| After conversion | Never show again (suppress by email/cookie) | They already converted |
| Multiple popup types | Max 1 popup per page load, max 2 per session | Prevents popup stacking |
| Across devices | Use authenticated state if available | Prevents re-showing to known users |

### Suppression Logic

```
If (user has dismissed popup X) → suppress for 14 days
If (user has submitted popup X) → suppress permanently
If (user has seen any popup this session) → suppress all popups for this page
If (user is logged in) → suppress lead-gen popups, show only relevant in-app prompts
If (user came from email link) → suppress email signup popups
```

## Mobile Considerations

### Mobile Popup Checklist

- [ ] Popup takes up less than 70% of viewport height
- [ ] Close button is easily tappable (44x44px minimum, top-right corner)
- [ ] Form fields use appropriate mobile keyboard types
- [ ] Text is readable without zooming (minimum 16px body)
- [ ] CTA button is full-width and at least 48px tall
- [ ] Popup does not trigger Google's intrusive interstitial penalty
- [ ] Exit intent alternative works (scroll-up, back button, or inactivity)
- [ ] Popup does not prevent scrolling or interaction with the page beneath
- [ ] Loading the popup does not cause layout shift

### Google Interstitial Guidelines

Google may penalize mobile pages that show intrusive interstitials. Exempt scenarios:
- Cookie consent / GDPR
- Age verification
- Paywalls for content behind login
- Small banners that take up "reasonable" screen space

Everything else (email popups, promo modals, full-screen ads) risks ranking penalties if shown immediately on mobile page load.

## A/B Testing Popups

### What to Test (Prioritized)

| Element | Impact Level | Test Example |
|---|---|---|
| **Trigger timing** | Very High | Exit intent vs 30-second delay vs 50% scroll |
| **Offer/value** | Very High | Ebook vs discount vs free trial |
| **Headline copy** | High | Benefit-focused vs curiosity-driven |
| **Popup format** | High | Center modal vs slide-in vs bar |
| **CTA copy** | Medium | "Get the guide" vs "Download free" |
| **Design/image** | Medium | With hero image vs text-only |
| **Field count** | Medium | Email only vs email + name |
| **Dismiss copy** | Low | Neutral vs negative opt-out |

### Popup Metrics to Track

| Metric | Definition | Benchmark |
|---|---|---|
| **View rate** | % of visitors who see the popup | Depends on targeting (20-80%) |
| **Close rate** | % who dismiss without acting | 85-95% (high is normal) |
| **Conversion rate** | % who complete the desired action | 3-10% for email, 1-5% for trial |
| **Engagement rate** | % who interact (click field, hover CTA) but don't convert | Diagnostic — high = copy/form issue |
| **Bounce impact** | Does the popup increase page bounce rate? | Should be <5% increase |
| **Revenue per visitor** | Does the popup improve overall RPV including downstream? | Must be net positive |

## Popup Playbook by Goal

### Email List Growth
- **Trigger**: Exit intent on blog content
- **Offer**: Content upgrade relevant to the article topic
- **Copy**: "Get the [topic] checklist — free"
- **Fields**: Email only
- **Frequency**: Once per session, suppressed 14 days after dismiss

### E-commerce Discount
- **Trigger**: Exit intent on product/cart pages
- **Offer**: First-purchase discount (10-15%)
- **Copy**: "Before you go — here's 10% off your first order"
- **Fields**: Email (to send the code)
- **Frequency**: Once per session, suppressed on purchase

### SaaS Free Trial
- **Trigger**: 60% scroll depth on feature pages
- **Offer**: Free trial or demo
- **Copy**: "See [Product] in action — free for 14 days"
- **Fields**: Email (or link to signup page)
- **Frequency**: Once per session, suppressed for logged-in users

### Webinar/Event Registration
- **Trigger**: Time delay (20s) on relevant content pages
- **Offer**: Upcoming event
- **Copy**: "[Speaker name] is teaching [topic] live — seats are limited"
- **Fields**: Email + first name
- **Frequency**: Once per day until event date

## Audit Output Format

When auditing a popup, deliver:

### 1. Strategic Assessment
Should this popup exist? Is the timing, targeting, and offer appropriate for the page and audience?

### 2. Copy Review
Headline, body, CTA, and dismiss copy — with 2-3 alternatives for each.

### 3. Design and UX Review
Layout, sizing, close button, mobile behavior, animation.

### 4. Targeting and Frequency Review
Who sees it, when, how often, and suppression rules.

### 5. Test Recommendations
Prioritized A/B test ideas with hypotheses.

## Related Skills
- [page-cro](../page-cro/SKILL.md) — Optimize the underlying page that the popup appears on
- [form-cro](../form-cro/SKILL.md) — Optimize the form inside the popup
- [ab-test-setup](../ab-test-setup/SKILL.md) — Design rigorous tests for popup variations
- [onboarding-cro](../onboarding-cro/SKILL.md) — Post-conversion onboarding for popup-captured leads
