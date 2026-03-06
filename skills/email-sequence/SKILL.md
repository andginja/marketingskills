---
name: email-sequence
description: |
  Design lifecycle and nurture email sequences for SaaS, e-commerce, and B2B.
  Covers welcome series, onboarding, re-engagement, upsell, winback, and cart abandonment.
  Trigger phrases: "email sequence", "drip campaign", "welcome series", "onboarding emails",
  "nurture sequence", "email automation", "lifecycle emails", "re-engagement email",
  "winback email", "cart abandonment email", "upsell email", "email flow"
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags: [email, sequences, lifecycle, automation, nurture, onboarding]
---

# Lifecycle and Nurture Email Sequences

## Purpose

Design email sequences that move people through the customer lifecycle — from first contact to loyal customer. Each sequence type has a different job, different timing, and different measure of success. This skill covers strategy, structure, copy direction, and timing for every major sequence type.

## Step 1: Gather Context

Before designing any sequence, clarify:

1. **Business model:** SaaS, e-commerce, B2B services, marketplace, or other?
2. **Product / offer:** What does the customer get? What's the core value moment?
3. **Audience segments:** Who receives this sequence? (New sign-ups, trial users, churned customers, etc.)
4. **Current email stack:** What platform are they using? (Affects automation capabilities)
5. **Existing sequences:** What's already running? (Avoid conflicts and redundancy)
6. **Key metrics to improve:** Open rate, click rate, conversion, retention, revenue?

## Step 2: Universal Email Principles

These apply to every sequence type.

### One Email, One Job
- Each email should have a single purpose and a single CTA.
- Do not combine onboarding guidance with an upsell pitch.
- If you're tempted to add "P.S. check out our new feature" — that's a separate email.

### Subject Line Fundamentals
- Keep under 50 characters (mobile truncation starts at 40-50).
- Front-load the most important words — they may get cut off.
- Personalize when it adds value (first name, company name, product used).
- Avoid ALL CAPS, excessive punctuation (!!!), and spam-trigger words.
- A/B test subject lines on every major send.

### From Name Strategy
- Use a real person's name for relationship-driven emails: "Sarah from Acme"
- Use the company name for transactional or product emails: "Acme"
- Be consistent within a sequence — don't switch from names between emails.
- The from name is often the single biggest factor in open rates.

### Preview Text
- The preview text (preheader) is your second headline. Do not waste it.
- Never let it default to "View this email in your browser."
- Write it intentionally to complement the subject line.

### Email Length
- **Transactional / action emails:** 50-100 words.
- **Educational / nurture emails:** 100-250 words.
- **Story-driven / narrative emails:** 200-400 words max.
- Shorter is almost always better. Respect the reader's time.

## Step 3: Sequence Types

---

### 3A: Welcome Series

**Purpose:** Set expectations, build trust, and drive the first key action.

**Trigger:** New subscriber, new account creation, or new customer.

**Sequence (4-6 emails over 10-14 days):**

| Email | Timing | Subject Pattern | Job |
|-------|--------|----------------|-----|
| 1 | Immediate | "Welcome to [Product]" / "You're in" | Deliver promised asset, set expectations for what emails to expect |
| 2 | Day 1-2 | "The fastest way to [key outcome]" | Drive first key action (setup, first use, profile completion) |
| 3 | Day 3-4 | Story / mission email | Build emotional connection — why the company exists, who it serves |
| 4 | Day 5-7 | Social proof | Share a customer result or case study that matches their segment |
| 5 | Day 8-10 | Best content / resource | Share your single most valuable piece of content |
| 6 | Day 12-14 | "What's next" / offer | Introduce the next step (upgrade, demo, deeper engagement) |

**Key Rules:**
- Email 1 should arrive within 60 seconds of sign-up. Delay kills engagement.
- Don't sell in emails 1-3. Earn trust first.
- Email 1 open rates should be 60-80%. If lower, check deliverability and from-name recognition.
- Segment the series if possible: different welcome paths for different sign-up sources or personas.

---

### 3B: Onboarding Drip

**Purpose:** Guide new users to their "aha moment" — the first time they experience core value.

**Trigger:** Account creation or trial start.

**Sequence (5-7 emails over 14-21 days):**

| Email | Timing | Focus | CTA |
|-------|--------|-------|-----|
| 1 | Immediate | Quick-start: the one thing to do first | Complete setup step 1 |
| 2 | Day 1 | Show the core feature in action (screenshot or GIF) | Try the core feature |
| 3 | Day 3 | Address the most common stuck point | Complete the action most users abandon |
| 4 | Day 5 | Social proof from a similar user | "See how [company] uses it" |
| 5 | Day 7 | Feature discovery — show a useful feature they haven't tried | Try the feature |
| 6 | Day 10 | Progress check / milestone | Celebrate what they've done, suggest next step |
| 7 | Day 14 | Trial ending (if applicable) | Upgrade CTA with clear value recap |

**Key Rules:**
- Trigger emails based on behavior, not just time. If they completed step 1, skip the reminder.
- Suppress onboarding emails once the user has activated (reached the aha moment).
- Include a "reply to this email if you're stuck" in every onboarding email. Real replies build relationships and surface product issues.
- Track which onboarding step has the highest drop-off and address it with a dedicated email.

**Behavioral Triggers to Build:**
- User signed up but hasn't logged in → remind within 24 hours.
- User started setup but didn't complete it → send setup completion email.
- User completed setup but hasn't used core feature → nudge to core feature.
- User used core feature → skip to advanced features.
- User hasn't logged in for 3+ days → re-engagement nudge (not full re-engagement sequence yet).

---

### 3C: Re-Engagement Sequence

**Purpose:** Win back inactive subscribers or users before removing them from the list.

**Trigger:** No opens in 60-90 days (subscribers) or no login in 30-60 days (product users).

**Sequence (3-4 emails over 14-21 days):**

| Email | Timing | Approach | Subject Pattern |
|-------|--------|----------|----------------|
| 1 | Day 0 | Value reminder — share your best content or newest feature | "Things have changed at [Product]" |
| 2 | Day 5-7 | Direct ask — "Still interested?" with a clear value prop | "Still want [key benefit]?" |
| 3 | Day 10-12 | Incentive (if appropriate) — discount, extended trial, free resource | "A gift before you go" |
| 4 | Day 14-21 | Final notice — "We'll stop emailing unless you click" | "Should we stop emailing you?" |

**Key Rules:**
- The last email should include a re-confirm link. If they don't click, remove them or move to a suppression list.
- Do not fear list shrinkage. A smaller, engaged list outperforms a large, disengaged one.
- Removing inactive contacts improves deliverability for everyone else on the list.
- Re-engagement subject lines should be different from your usual style — pattern interruption.

---

### 3D: Upsell / Cross-Sell Sequence

**Purpose:** Expand revenue from existing customers by introducing higher tiers or complementary products.

**Trigger:** Usage threshold hit, feature limit approaching, time-based milestone, or complementary product fit signal.

**Sequence (3-4 emails over 10-14 days):**

| Email | Timing | Focus |
|-------|--------|-------|
| 1 | Trigger event | Show the value they've already gotten + what they're missing |
| 2 | Day 3-4 | Social proof — customer who upgraded and saw results |
| 3 | Day 7 | Direct comparison — what they have now vs. what the upgrade includes |
| 4 | Day 10-14 | Limited-time offer or personal outreach from account manager |

**Key Rules:**
- Never upsell a customer who is unhappy. Check support tickets and NPS before triggering.
- Lead with the value gap: "You've used 90% of your monthly exports. Upgrade to unlimited."
- Usage-based triggers outperform time-based triggers for upsell.
- Frame the upgrade as "unlock what you need" not "buy our more expensive thing."

**Subject Line Patterns:**
- "You're outgrowing [current plan]"
- "Unlock [specific feature] for your team"
- "[Company name] — you've hit [milestone]"
- "What [similar company] did at your stage"

---

### 3E: Winback Sequence

**Purpose:** Re-engage customers who have cancelled or churned.

**Trigger:** Subscription cancelled, account closed, or last purchase was 90+ days ago.

**Sequence (3-5 emails over 30-60 days):**

| Email | Timing | Approach |
|-------|--------|----------|
| 1 | Day 0-3 post-churn | Acknowledge departure, ask for feedback (brief survey or reply) |
| 2 | Day 14 | Share what's new — focus on improvements that address common churn reasons |
| 3 | Day 30 | Offer incentive to return (discount, extended trial, concierge onboarding) |
| 4 | Day 45-60 | Final outreach — personal note from founder or account lead |
| 5 | Day 90 | Annual check-in (only if not re-engaged) |

**Key Rules:**
- Segment by churn reason. Someone who left because of price needs a different email than someone who left because of a missing feature.
- Email 1 should be plain text, from a real person, and feel genuinely curious — not desperate.
- If they gave a reason for leaving and you've fixed that issue, lead with that in email 2 or 3.
- Winback offers should be genuine. "Come back and get 3 months free" works. "Come back, nothing has changed" doesn't.
- Do not winback customers who left because of a bad experience without first addressing what went wrong.

---

### 3F: Cart Abandonment Sequence (E-commerce)

**Purpose:** Recover abandoned carts and complete the purchase.

**Trigger:** Item added to cart, checkout started but not completed.

**Sequence (3 emails over 48-72 hours):**

| Email | Timing | Approach |
|-------|--------|----------|
| 1 | 1-2 hours | Reminder — "You left something behind." Show the product, direct link to cart. |
| 2 | 24 hours | Handle objections — reviews, satisfaction guarantee, shipping info, sizing help. |
| 3 | 48-72 hours | Incentive — small discount (5-10%), free shipping, or bundle offer. |

**Key Rules:**
- Email 1 should not offer a discount. Many people abandoned by accident or got distracted. A simple reminder converts 5-10% on its own.
- Include a product image and a direct "return to cart" link in every email.
- Show star ratings and a short review snippet in email 2.
- Train customers to wait for discounts and your margins will erode. Use discounts sparingly — only in email 3, and only for carts above a certain value.
- Segment: first-time buyers get the full sequence. Repeat customers may only need email 1.

## Step 4: Segmentation Strategy

### Segment By These Dimensions
1. **Lifecycle stage:** Subscriber, trial user, active customer, churned.
2. **Engagement level:** Active (opened in last 30 days), passive (30-90 days), inactive (90+ days).
3. **Behavior:** Features used, actions taken, pages visited, content downloaded.
4. **Persona / role:** Decision-maker vs. end-user. Technical vs. non-technical.
5. **Source:** How they entered the list (organic, paid, referral, event).
6. **Purchase history:** First-time buyer, repeat buyer, high-value, low-value.

### Segmentation Rules
- Start simple. Two to three segments are better than twenty poorly maintained ones.
- Every segment should have a different message or different timing — if the emails are the same, you don't need the segment.
- Review and prune segments quarterly. Dead segments cause operational overhead.

## Step 5: Timing and Cadence

### General Timing Guidelines
| Sequence Type | Frequency | Total Duration |
|--------------|-----------|---------------|
| Welcome | Daily for 2-3 days, then every 2-3 days | 10-14 days |
| Onboarding | Every 2-3 days, behavior-triggered | 14-21 days |
| Nurture | Weekly or bi-weekly | Ongoing |
| Re-engagement | Every 5-7 days | 14-21 days |
| Cart abandonment | Hours 1, 24, 48-72 | 3 days |
| Winback | Every 14-30 days | 60-90 days |

### Timing Optimization
- **Best send times vary by audience.** B2B: Tuesday-Thursday, 9-11 AM recipient's timezone. E-commerce: evenings and weekends often outperform.
- **Use send-time optimization** if your platform supports it (most major ESPs do).
- **Respect frequency caps.** No contact should receive more than 1 automated email per day, regardless of how many sequences they qualify for.
- **Prioritize sequences.** Onboarding trumps nurture. Cart abandonment trumps promotional. Build a priority hierarchy.

## Step 6: Deliverability Best Practices

### Authentication
- Set up SPF, DKIM, and DMARC for your sending domain. Non-negotiable.
- Use a dedicated sending subdomain (e.g., mail.yourdomain.com) to protect your primary domain reputation.

### List Hygiene
- Remove hard bounces immediately.
- Suppress contacts who haven't opened in 90 days (or move to re-engagement).
- Use double opt-in for new subscribers when feasible.
- Never buy email lists. The deliverability damage outweighs any short-term gain.

### Content
- Keep image-to-text ratio reasonable. Text-heavy emails deliver better than image-heavy ones.
- Avoid URL shorteners in email body — they trigger spam filters.
- Include a plain-text version of every HTML email.
- Use a consistent from address. Frequent changes hurt sender reputation.

### Monitoring
- Track deliverability rate (should be 95%+), bounce rate (under 2%), and spam complaint rate (under 0.1%).
- Monitor inbox placement, not just delivery. Tools: GlockApps, Litmus, or Mailgun's inbox placement testing.
- If deliverability drops, reduce volume and focus on most-engaged segments to rebuild reputation.

## Step 7: Measurement

### Key Metrics by Sequence Type
| Sequence | Primary Metric | Secondary Metrics |
|----------|---------------|-------------------|
| Welcome | Activation rate (completed first action) | Open rate, click rate |
| Onboarding | Feature adoption, aha-moment reached | Time to value, support tickets |
| Re-engagement | Re-activation rate | List cleaned (removed inactives) |
| Upsell | Upgrade conversion rate | Revenue per email, ARPU change |
| Winback | Return rate | Revenue recovered, feedback collected |
| Cart abandonment | Cart recovery rate | Revenue recovered, AOV of recovered carts |

### Benchmarks (Use as Directional, Not Absolute)
- **Welcome email open rate:** 50-70%
- **Sequence average open rate:** 25-40%
- **Click-to-open rate:** 10-20%
- **Cart abandonment recovery:** 5-15% of abandoned carts
- **Unsubscribe rate:** Under 0.5% per email

## Output Format

When designing an email sequence, deliver:

1. **Sequence overview** — purpose, trigger, audience, success metric.
2. **Email-by-email breakdown** — for each email: timing, subject line (2-3 options), body copy or detailed copy direction, CTA.
3. **Segmentation notes** — who gets this sequence, who is excluded, and any branching logic.
4. **Behavioral triggers** — what actions should modify or skip emails in the sequence.
5. **Measurement plan** — what to track, what benchmarks to target, when to optimize.
6. **Assumptions** — anything assumed about the audience, product, or tech stack.
