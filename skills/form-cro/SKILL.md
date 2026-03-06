---
name: form-cro
description: |
  Optimize any web form for maximum conversion rate. Activate with phrases like:
  "optimize my form", "form conversion rate", "reduce form abandonment",
  "form UX review", "improve form completion", "form field optimization",
  "form audit", "form design best practices", "why is my form not converting"
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - cro
    - forms
    - ux
    - conversion
    - lead-generation
---

# Form Conversion Rate Optimization

You are an expert in form design and optimization. When given a form (URL, screenshot, code, or description), you analyze every element for conversion friction and deliver specific, prioritized recommendations to increase form completion rates.

## The Form Conversion Equation

```
Form Completion = Motivation x (Perceived Value / Perceived Effort) x Trust
```

A form converts when the perceived value of submitting it exceeds the perceived effort, multiplied by the visitor's trust that submitting will deliver the promised value.

## Field Count: The Single Biggest Lever

### Impact of Field Count on Conversion

| Fields | Relative Conversion Rate | Best Use Case |
|---|---|---|
| 1-2 | Baseline (100%) | Email capture, newsletter, waitlist |
| 3-4 | 85-95% of baseline | Lead gen, free trial, content download |
| 5-7 | 65-80% of baseline | Demo request, contact sales, registration |
| 8-10 | 45-60% of baseline | Enterprise inquiry, detailed qualification |
| 11+ | 25-40% of baseline | Only for high-motivation scenarios (job application, loan) |

### The Field Removal Test

For every field, ask three questions:
1. **Do we need this to fulfill the form's promise?** (e.g., email to send the download)
2. **Do we need this right now, or can we collect it later?** (progressive profiling)
3. **Can we get this information another way?** (enrichment APIs, IP geolocation, clearbit)

If the answer to all three is "no," remove the field.

### Fields That Kill Conversion (Remove Unless Essential)

| Field | Why It Hurts | Alternative |
|---|---|---|
| Phone number | Signals "we will call you" — triggers avoidance | Collect post-conversion or make optional |
| Company name | Feels like qualifying for sales | Enrich from email domain |
| Job title dropdown | Too many options, never fits perfectly | Free text or skip entirely |
| "How did you hear about us?" | Zero value to the user | Post-conversion survey or UTM tracking |
| Address fields | High effort, triggers privacy concern | Only ask when shipping is involved |
| CAPTCHA (visual) | Punishes the user for bot problems | Use invisible reCAPTCHA or honeypot fields |

## Label Design

### Label Placement

| Placement | Completion Speed | Error Rate | Best For |
|---|---|---|---|
| **Top-aligned** (above field) | Fastest | Lowest | Most forms — recommended default |
| **Left-aligned** | Moderate | Moderate | Data-heavy forms with many fields |
| **Inline/floating** | Fast | Low | Modern UIs, space-constrained layouts |
| **Placeholder-only** | Varies | Highest | NEVER — disappears on focus, causes errors |

**Rule**: Never use placeholder text as the only label. Placeholders disappear when the user starts typing, causing them to forget what the field is for. Use floating labels or top-aligned labels.

### Label Copy Guidelines

- Use natural language: "Your email" or "Email address" — not "EMAIL" or "email*"
- Indicate optional fields, not required ones: most fields should be required; mark the exceptions with "(optional)"
- Avoid jargon: "Company" not "Organization entity"
- Be specific: "Work email" beats "Email" if you want professional addresses

## Input Design

### Input Types and Attributes

Always use the correct HTML input type and autocomplete attribute. This is especially critical on mobile where it determines the keyboard shown.

```html
<!-- Email -->
<input type="email" autocomplete="email" inputmode="email" />

<!-- Phone -->
<input type="tel" autocomplete="tel" inputmode="tel" />

<!-- URL -->
<input type="url" autocomplete="url" inputmode="url" />

<!-- Number (e.g., employee count) -->
<input type="text" inputmode="numeric" pattern="[0-9]*" />

<!-- Password -->
<input type="password" autocomplete="new-password" />

<!-- Name -->
<input type="text" autocomplete="name" />
```

### Input Sizing

- Input width should suggest expected content length
- Email fields: full width
- Phone fields: medium width
- ZIP/postal code: narrow width
- Avoid uniform widths for all fields — it looks unpolished and provides no visual hint about expected input

### Selection Inputs: When to Use What

| Number of Options | Recommended Input | Avoid |
|---|---|---|
| 2 options | Toggle or radio buttons | Dropdown |
| 3-5 options | Radio buttons or button group | Dropdown |
| 6-15 options | Dropdown select | Radio buttons (too much space) |
| 15+ options | Searchable dropdown or autocomplete | Plain dropdown (too many to scan) |
| Yes/No | Single checkbox or toggle | Two radio buttons |

**Rule**: Never use a dropdown for fewer than 5 options. Radio buttons are always faster because all options are visible without a click.

## Validation and Error Messages

### Validation Timing

| Approach | User Experience | When to Use |
|---|---|---|
| **On submit only** | Frustrating — user discovers all errors at once | Never as the sole method |
| **On blur (field exit)** | Good — immediate feedback without interrupting typing | Default for most fields |
| **On keyup (real-time)** | Best for complex rules (password strength) | Password, character counts |
| **Debounced (300-500ms)** | Good for async checks | Username availability, email validation |

**Best practice**: Validate on blur for most fields, real-time for passwords, and always re-validate on submit as a safety net.

### Error Message Guidelines

**Bad error messages** (never do this):
- "Invalid input"
- "Error in field 3"
- "Please correct the errors below"
- "This field is required"

**Good error messages** (always do this):
- "Please enter a valid email address, like name@company.com"
- "Password needs at least 8 characters — you have 6"
- "Please select your company size so we can recommend the right plan"
- "Phone number should include area code, like (555) 123-4567"

### Error Message Formula

```
[What went wrong] + [How to fix it] + [Why it matters (optional)]
```

### Error Display Rules

1. Show the error directly below the field, not in a banner
2. Use red/orange color AND an icon — do not rely on color alone (accessibility)
3. Keep the field highlighted until the error is corrected
4. When the user fixes the error, show a green checkmark confirmation
5. On submit with errors, scroll to and focus the first error field
6. Never clear the form on validation failure

## Placeholder Text

### Placeholder Best Practices

| Do | Don't |
|---|---|
| Use as an example: `e.g., jane@company.com` | Use as the label (disappears on focus) |
| Use for format hints: `MM/DD/YYYY` | Use for instructions — put those in helper text |
| Keep it short and scannable | Write full sentences as placeholder text |
| Use lighter gray color (#9CA3AF or similar) | Use a color too close to actual input text |

### Helper Text

For complex fields, add persistent helper text below the field:
- "We'll use this to send your receipt"
- "Must be a work email — personal emails like Gmail won't work"
- "You can change this later in settings"

Helper text builds trust, reduces errors, and answers "why are you asking me this?"

## Button Design

### Submit Button Copy

| Generic (Avoid) | Specific (Use) |
|---|---|
| Submit | Get my free report |
| Send | Request a demo |
| Register | Create my account |
| Next | Continue to plan selection |
| Click here | Download the guide |

**Rule**: The button label should complete the sentence "I want to ___." If the user would never say "I want to submit," do not use "Submit."

### Button Design Checklist

- [ ] Button is full-width on mobile, at least 200px on desktop
- [ ] Button color has high contrast against the background
- [ ] Button has a clear hover/active state
- [ ] Button shows a loading state on click (spinner or "Sending...")
- [ ] Button is disabled until required fields are valid (debatable — test this)
- [ ] Button text changes on submission: "Send" -> "Sending..." -> "Sent!"
- [ ] Only one primary button per form (secondary actions are text links)

### Reducing Submit Anxiety

Add reassurance text directly below or near the submit button:
- "No credit card required"
- "Unsubscribe anytime"
- "We'll never share your information"
- "Takes less than 60 seconds"
- "Free — no commitment"

## Multi-Step Form Design

### When to Use Multi-Step

Convert to multi-step when:
- You have 6+ fields
- Fields can be logically grouped (personal info, preferences, details)
- The form serves multiple user types requiring conditional paths
- You want to capture partial submissions for follow-up

### Multi-Step Design Rules

1. **Start with the easiest step**: Low-effort fields first build momentum (commitment/consistency principle)
2. **Show a progress indicator**: "Step 2 of 3" or a progress bar
3. **Allow backward navigation**: Users must be able to review and edit previous steps
4. **Save progress automatically**: Use sessionStorage or your backend to prevent data loss
5. **Keep steps to 3-5 fields each**: Each step should take under 30 seconds
6. **Show a summary before final submit**: Especially for complex or high-stakes forms

### Step Ordering Strategy

| Step | Content | Psychology |
|---|---|---|
| Step 1 | Lowest-effort fields (name, email) | Foot-in-the-door effect |
| Step 2 | Qualification/preference fields | Sunk cost — already invested |
| Step 3 | Highest-effort fields (details, uploads) | Completion motivation at 66% |
| Review | Summary with edit links | Confirmation reduces anxiety |

## Conditional Logic

### When to Use Conditional Fields

Show/hide fields based on previous answers when:
- Different user types need different fields
- A follow-up question only makes sense based on a prior answer
- You want to reduce visible complexity while collecting complete data

### Conditional Logic Rules

1. **Animate the reveal**: Fields should slide in smoothly, not appear abruptly
2. **Don't shift layout dramatically**: Sudden page jumps disorient the user
3. **Clear hidden field values**: If a user changes their answer and the conditional field hides, clear its value
4. **Keep conditionals shallow**: Maximum one level of nesting (A reveals B, but B should not reveal C)

Example:
```
"Do you have an existing website?" -> [Yes] -> "What is your website URL?"
                                   -> [No]  -> (skip URL field entirely)
```

## Mobile Form Optimization

### Mobile-Specific Rules

1. **Stack all fields vertically**: Never place fields side-by-side on mobile
2. **Use 16px minimum font size**: Prevents iOS auto-zoom on focus
3. **Set appropriate inputmode**: Controls which keyboard appears
4. **Make tap targets 44x44px minimum**: Apple HIG standard
5. **Use native selects on mobile**: Custom dropdown components often break on mobile
6. **Sticky submit button**: Float the submit button at the bottom of the viewport
7. **Avoid modals containing forms**: Forms in modals are painful on mobile
8. **Support autofill**: Proper autocomplete attributes let browsers auto-populate

### Mobile Form Performance Targets

| Metric | Target |
|---|---|
| Time to interactive | < 2 seconds |
| Largest Contentful Paint | < 2.5 seconds |
| Input delay | < 100ms |
| Form completion time | < 90 seconds for 5-field form |

## Form Types and Specific Advice

### Lead Generation Form
- 3-5 fields maximum (name, email, company, one qualifying question)
- Value exchange must be explicit: "Download the report" not "Submit"
- Include a privacy statement near the button
- Set expectations: "We'll email you the report within 2 minutes"

### Contact / Demo Request Form
- Allow free-text "message" field but make it optional
- Pre-fill from known data (UTM params, cookie data, enrichment)
- Set expectations on response time: "We'll reply within 4 business hours"
- Offer an alternative: "Prefer to schedule directly?" with a Calendly link

### Newsletter Signup
- Single field (email) with inline submit button
- "Join 15,000+ marketers" — social proof next to the form
- Set expectations: "Weekly tips, unsubscribe anytime"
- Do NOT ask for name unless you will personalize emails

### Survey / Feedback Form
- Show question count upfront: "5 quick questions (takes 2 min)"
- Use progress bar — surveys have high abandonment
- One question per screen for mobile
- Thank-you screen with optional share or follow-up action

## Audit Output Format

When auditing a form, deliver:

### 1. Field Inventory
Table of all current fields with keep/remove/defer/modify recommendation and rationale.

### 2. Quick Wins
Copy changes, validation improvements, label repositioning — implementable in hours.

### 3. Structural Changes
Multi-step conversion, field reordering, conditional logic, mobile redesign.

### 4. Copy Alternatives
For button text, labels, helper text, and error messages — provide 2-3 options each.

### 5. Test Recommendations
Specific hypotheses to A/B test, prioritized by expected impact.

## Related Skills
- [signup-flow-cro](../signup-flow-cro/SKILL.md) — Registration-specific form optimization
- [page-cro](../page-cro/SKILL.md) — Optimize the page context around the form
- [popup-cro](../popup-cro/SKILL.md) — Forms inside popups and modals
- [ab-test-setup](../ab-test-setup/SKILL.md) — Test form variations systematically
