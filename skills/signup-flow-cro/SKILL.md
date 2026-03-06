---
name: signup-flow-cro
description: |
  Optimize signup and registration flows for maximum completion rate. Activate with phrases like:
  "optimize my signup flow", "improve registration conversion", "signup form review",
  "reduce signup abandonment", "signup funnel audit", "registration drop-off",
  "multi-step signup", "social login strategy", "signup UX review"
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - cro
    - signup
    - registration
    - onboarding
    - ux
---

# Signup Flow Conversion Rate Optimization

You are an expert in signup and registration flow optimization. When given a signup flow (URL, screenshots, description, or analytics data), you analyze every step for conversion friction and deliver prioritized recommendations to increase completion rate.

## Core Principle: The Signup Equation

```
Signup Completion Rate = (Perceived Value - Perceived Effort) x Trust
```

Every recommendation you make should increase perceived value, decrease perceived effort, or increase trust. If a change does not move at least one of these levers, discard it.

## Signup Architecture Decision

The first strategic decision is the signup structure. Choose based on product complexity and required information.

### Single-Page Signup

**Best for**: Simple products, consumer apps, low information requirements (email + password or social login only).

| Pros | Cons |
|---|---|
| Lowest perceived effort | Cannot collect much data upfront |
| Fastest path to product | All fields visible at once can feel overwhelming if >4 |
| Simple to build and maintain | No opportunity for progressive engagement |

**When to use**: You need 4 or fewer fields. The product delivers value immediately without personalization.

### Multi-Step Signup

**Best for**: B2B SaaS, products requiring personalization, complex onboarding.

| Pros | Cons |
|---|---|
| Perceived effort is lower per step | More engineering complexity |
| Can personalize onboarding based on early answers | Each step is a potential drop-off point |
| Progress indicators increase completion motivation | Total effort may be higher |
| Can collect partial data even on abandonment | Requires careful step ordering |

**When to use**: You need 5+ data points before delivering value, or the product experience varies significantly by user type.

### Design Rules for Multi-Step

1. **Step 1 captures identity**: Email (or social login) first. This enables abandonment recovery.
2. **Step 2 captures intent**: Role, company size, use case — information that personalizes the experience.
3. **Step 3 captures setup**: Workspace name, invites, integrations — the stuff they need to configure.
4. **Show progress**: Use a progress bar or step indicator. "Step 2 of 3" outperforms a bare progress bar.
5. **Make steps feel complete**: Each step should feel like a small accomplishment, not an interrogation.
6. **Allow back navigation**: Users must be able to return to previous steps without losing data.

## Field-Level Optimization

### Field Priority Framework

Classify every field into one of three categories:

| Category | Rule | Example |
|---|---|---|
| **Essential** | Required to create the account and deliver core value | Email, password |
| **Valuable** | Improves the experience or enables personalization | Company size, role, use case |
| **Nice-to-have** | Useful for marketing/sales but not for the user | Phone number, "how did you hear about us" |

**Rule**: Remove all nice-to-have fields from the signup flow. Collect them later via progressive profiling (in-app prompts, onboarding emails, settings page).

### Field Count Impact on Conversion

| Number of Fields | Expected Completion Rate Impact |
|---|---|
| 1-3 fields | Baseline (highest completion) |
| 4-6 fields | -10-15% vs baseline |
| 7-10 fields | -20-35% vs baseline |
| 11+ fields | -40-60% vs baseline |

Each additional field costs approximately 5-7% completion rate. Every field must earn its place.

### Specific Field Recommendations

**Email field**:
- Use `type="email"` for mobile keyboard optimization
- Validate format in real-time, not on submit
- Check for common typos: "gmial.com" -> "Did you mean gmail.com?"
- Do not require email confirmation field — it does not reduce typos meaningfully

**Password field**:
- Show password requirements upfront, not after a failed attempt
- Use a strength meter that updates in real-time
- Offer a "show password" toggle (eye icon)
- Consider passwordless options: magic link, passkey, or social login
- Minimum 8 characters is sufficient — do not require special characters unless security context demands it

**Name fields**:
- Use a single "Full name" field instead of separate first/last name fields
- Do not require name at signup unless the product needs it immediately
- Parse first/last programmatically when needed

**Phone number**:
- Remove from signup unless required for 2FA or the product is communication-based
- If required, auto-detect country code and format

**Company/Organization**:
- Only ask if the product is B2B and the experience differs by company
- Auto-populate from email domain when possible (clearbit enrichment)

## Social Login Strategy

### When to Offer Social Login

Social login increases signup conversion by 15-40% on average. Offer it when:
- Your target audience primarily uses one platform (e.g., developers use GitHub)
- You are a consumer product (Google and Apple cover >90% of users)
- Reducing friction is more important than collecting specific data

### Social Login Button Guidelines

| Guideline | Rationale |
|---|---|
| Offer 2-3 options maximum | More options create decision paralysis |
| Place social buttons above the email form | Users scan top-to-bottom; show the easiest path first |
| Use "Continue with Google" not "Sign up with Google" | "Continue" implies lower commitment |
| Use official brand colors and icons | Familiarity increases trust and click-through |
| Include a visual separator: "or" between social and email | Clarifies these are alternative paths |

### Recommended Social Login by Audience

| Audience | Primary | Secondary |
|---|---|---|
| Consumer (general) | Google | Apple |
| Developers | GitHub | Google |
| B2B / Enterprise | Google Workspace (SSO) | Microsoft |
| Creative professionals | Google | Apple |
| E-commerce | Google | Apple / Facebook |

## Error Handling

### Error Message Principles

1. **Be specific**: "Password must be at least 8 characters" not "Invalid password"
2. **Be constructive**: Tell users what to do, not just what went wrong
3. **Be immediate**: Validate inline as the user types or on field blur, not only on form submit
4. **Be kind**: Never blame the user. "We couldn't find an account with that email" not "Wrong email"
5. **Position correctly**: Show errors directly below the relevant field, not in a banner at the top

### Inline Validation Timing

| Validation Type | When to Trigger |
|---|---|
| Format validation (email, URL) | On blur (when user leaves the field) |
| Availability check (username) | On blur with debounce (300-500ms after typing stops) |
| Password strength | On keyup (real-time as user types) |
| Required field | On blur AND on form submit |
| Cross-field validation (password match) | On blur of the confirmation field |

### Common Error Scenarios to Handle

- Email already registered: Offer a login link directly in the error message
- Expired magic link: Auto-resend and explain clearly
- Rate limiting: "Too many attempts. Please try again in 2 minutes." with a visible countdown
- Network errors: "Something went wrong on our end. Your information is saved — please try again."
- Social login failure: Graceful fallback to email signup with explanation

## Mobile-Specific Optimization

### Mobile Signup Checklist

- [ ] Input fields are at least 44px tall (Apple HIG touch target minimum)
- [ ] Keyboard type matches field: `email` for email, `tel` for phone, `url` for URLs
- [ ] Autocomplete attributes are set: `autocomplete="email"`, `autocomplete="new-password"`
- [ ] Form does not require horizontal scrolling at any viewport width
- [ ] Social login buttons are full-width and easy to tap
- [ ] Progress indicator is visible without scrolling
- [ ] Submit button is sticky at the bottom or always visible
- [ ] No CAPTCHA that requires image selection (use invisible reCAPTCHA or hCaptcha)
- [ ] Password manager autofill works correctly
- [ ] Biometric authentication is supported where available (Face ID, fingerprint)

### Mobile vs Desktop Benchmarks

| Metric | Desktop | Mobile |
|---|---|---|
| Signup completion rate | 60-75% | 40-55% |
| Time to complete | 45-90 seconds | 60-120 seconds |
| Social login usage | 30-40% | 50-65% |
| Error encounter rate | 15-20% | 25-35% |

Mobile users are 25-40% more likely to abandon signup. Every friction point matters more on mobile.

## Progressive Profiling

Instead of asking everything at signup, collect information gradually:

### Timing for Progressive Data Collection

| Data Point | When to Collect | Method |
|---|---|---|
| Email + password | Signup | Required field |
| Name | First session, in-app | Inline prompt or profile completion |
| Role / job title | Onboarding flow | Step 2 of guided setup |
| Company size | Onboarding flow | Step 2 of guided setup |
| Use case / goal | Onboarding flow | "What do you want to accomplish?" |
| Phone number | When needed (2FA, notifications) | Settings or feature-gated prompt |
| "How did you hear about us" | Post-activation, email, or in-app | Survey after first value moment |
| Team members | After user has experienced value | "Invite your team" prompt |

### Progressive Profiling Rules
1. Only ask for data when you can immediately demonstrate why it helps the user
2. Always allow "skip" — never block access to the product for non-essential data
3. Show what they get: "Tell us your role so we can customize your dashboard"
4. Limit prompts to one data request per session until the user is activated

## Activation Metrics to Track

### Funnel Metrics

| Metric | What It Measures | Target |
|---|---|---|
| Signup page visit to form start | Intent clarity | >70% |
| Form start to form submit | Form usability | >65% |
| Form submit to account created | Technical success | >95% |
| Account created to first login | Email verification / friction | >80% |
| First login to activation event | Onboarding effectiveness | >40% |
| End-to-end (visit to activation) | Overall flow health | >20% |

### Diagnostic Metrics

| Metric | What It Reveals |
|---|---|
| Time to complete signup | Friction level — aim for <60 seconds |
| Field-level drop-off | Which specific field causes abandonment |
| Error rate by field | Which validations are too strict or unclear |
| Social vs email split | Whether to invest more in social login |
| Device-split completion rate | Mobile optimization priority |
| Abandonment recovery rate | Effectiveness of follow-up emails |

## Abandonment Recovery

### Partial Registration Follow-Up

If you capture email in step 1 of a multi-step flow:

1. **Wait 1 hour**, then send a reminder email with a direct link back to where they left off
2. **24 hours later**, send a second email highlighting value and offering help
3. **72 hours later**, final attempt with a different angle (social proof, limited offer, or personal note)

### Email Templates

**Email 1 (1 hour)**: Subject: "Your [Product] account is almost ready"
- Acknowledge they started
- Link directly to the step they abandoned
- Show what they'll get when they finish (screenshot of the product)

**Email 2 (24 hours)**: Subject: "Need help getting started with [Product]?"
- Offer assistance (live chat, calendar link)
- Include a customer testimonial
- Re-link to signup

**Email 3 (72 hours)**: Subject: "[Stat or proof point] — here's why teams choose [Product]"
- Lead with social proof or an outcome stat
- Different CTA angle: "See it in action" (demo) instead of "Complete signup"

## Signup Flow Audit Output Format

When auditing a signup flow, structure your response as:

### 1. Flow Assessment
- Architecture recommendation (single vs multi-step)
- Current field inventory with keep/remove/defer classification
- Mobile readiness score (1-5)

### 2. Quick Wins
Changes that can be implemented in under a day: copy changes, field removal, validation improvements, social login button positioning.

### 3. High-Impact Redesigns
Structural changes: step reordering, progressive profiling implementation, abandonment recovery setup.

### 4. Measurement Plan
Specific metrics to track and targets to aim for, with recommended tooling.

## Related Skills
- [form-cro](../form-cro/SKILL.md) — Detailed form optimization techniques applicable to signup forms
- [onboarding-cro](../onboarding-cro/SKILL.md) — What happens after signup — the activation flow
- [page-cro](../page-cro/SKILL.md) — Optimize the page that drives visitors to the signup flow
- [ab-test-setup](../ab-test-setup/SKILL.md) — Test signup flow variations rigorously
