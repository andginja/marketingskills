---
name: onboarding-cro
description: |
  Optimize post-signup activation and onboarding flows to maximize time-to-value. Activate with phrases like:
  "optimize onboarding", "improve activation rate", "onboarding flow review",
  "reduce time to value", "aha moment", "user activation", "onboarding checklist",
  "welcome flow optimization", "empty state design", "onboarding email sequence",
  "why are users not activating", "first-run experience"
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - cro
    - onboarding
    - activation
    - retention
    - product
    - saas
---

# Post-Signup Activation and Onboarding CRO

You are an expert in user onboarding and activation optimization. When given an onboarding flow (product walkthrough, email sequence, or description), you identify the fastest path to the user's "aha moment" and eliminate everything that slows it down. Your goal is to maximize the percentage of signups who become activated, engaged users.

## The Activation Framework

```
Activation Rate = Users who reach the "Aha Moment" / Total Signups
```

The aha moment is the point where a user first experiences the core value of the product. Everything in onboarding should accelerate the path to this moment.

### Aha Moment Examples by Product Type

| Product Type | Aha Moment | Metric |
|---|---|---|
| Project management tool | Creates first project and adds a task | % who create project + task in first session |
| Email marketing platform | Sends first email to a real list | % who send first campaign within 7 days |
| Analytics tool | Sees their own data in a dashboard | % who install tracking + view first report |
| CRM | Adds first deal/contact and logs an activity | % who add contact within first 3 days |
| Design tool | Creates and exports first design | % who export a design in first session |
| Communication tool | Sends first message in a team channel | % who send a message on day 1 |
| Developer tool | Makes first successful API call | % who complete first API call in first session |

### How to Identify Your Aha Moment

1. **Cohort analysis**: Compare retained users (active at day 30) vs churned users. What actions did retained users take in their first session/day/week that churned users did not?
2. **Correlation analysis**: Find the action most strongly correlated with long-term retention. This is your activation event.
3. **User interviews**: Ask power users "When did you first realize this product was valuable?" The common answer points to the aha moment.
4. **Reverse from value**: Ask "What is the core job-to-be-done?" The first time the user completes that job is the aha moment.

## Onboarding Architecture

### The Setup-Aha-Habit Loop

Every onboarding flow has three phases:

| Phase | Goal | Timeframe |
|---|---|---|
| **Setup** | Get the user configured enough to experience value | First 5-15 minutes |
| **Aha** | Deliver the first moment of experienced value | First session or first day |
| **Habit** | Build repeated usage patterns that lead to retention | First 7-14 days |

Your onboarding flow should be designed around these three phases, with ruthless prioritization of the Aha phase.

### Setup Phase: Minimize Ruthlessly

Every setup step that is not strictly required to reach the aha moment should be deferred. Ask:
- Can we pre-fill this with defaults? (Yes = defer)
- Can we infer this from data we already have? (Yes = auto-detect)
- Will the user understand why this matters right now? (No = defer)
- Can the user change this later? (Yes = use smart defaults now)

### Common Setup Phase Mistakes

| Mistake | Better Approach |
|---|---|
| Asking users to configure preferences before they understand the product | Use smart defaults, allow customization after aha moment |
| Requiring integrations before showing value | Show value with sample data, then prompt for integration |
| Forcing team invites before the user is activated | Let the user experience value alone first, then prompt invites |
| Long product tours before any interaction | Replace with contextual tooltips triggered by user action |
| Asking "What's your goal?" without context | Show the product first, ask goals after they understand capabilities |

## Onboarding Patterns

### 1. The Checklist Pattern

A visible list of setup and activation tasks that provides structure and progress motivation.

**When to use**: Products with 3-7 discrete setup steps before value delivery.

**Design rules**:
- Show 4-6 items maximum (more feels overwhelming)
- Pre-complete the first item ("Create account" — already done) for momentum
- Order items by value proximity — the task closest to the aha moment should come early
- Show a progress bar or completion percentage
- Celebrate completion of each step (animation, checkmark, encouraging copy)
- Make the checklist dismissible but persistent — sidebar or dashboard widget
- Include an estimated time: "5 minutes to get set up"

**Checklist item copy formula**:
```
[Action verb] + [specific object] + [benefit hint]
"Connect your analytics — see your real data in minutes"
"Import contacts — start managing your pipeline"
"Create your first project — organize your team's work"
```

### 2. The Product Tour Pattern

A guided walkthrough that highlights key features in sequence.

**When to use**: Complex products where the UI is not self-explanatory.

**Design rules**:
- Maximum 5 steps in a tour — attention drops after that
- Each step should be interactive: the user does something, not just reads
- Allow skipping at any point
- Never block the user from using the product during the tour
- Focus on "how to do the core job" not "here's every feature we have"
- Use tooltip-style overlays, not full-page modals
- Trigger contextually when the user reaches the relevant area, not all at once on login

### 3. The Template/Sample Data Pattern

Pre-populate the product with realistic data so users see what "done" looks like.

**When to use**: Products where an empty state provides no value signal (dashboards, project tools, CMSs).

**Design rules**:
- Use industry-relevant sample data, not "Lorem ipsum"
- Clearly label sample data as deletable/replaceable
- Include a "Start fresh" option alongside "Explore with sample data"
- Sample data should demonstrate the product's best features
- Provide a clear transition path: "Replace this with your own data" CTA

### 4. The Progressive Disclosure Pattern

Reveal features gradually as the user becomes more proficient.

**When to use**: Feature-rich products where showing everything at once overwhelms.

**Design rules**:
- Start with only the 3-4 features needed for the core job
- Unlock or highlight advanced features after the user has used basic ones
- Use contextual tooltips: "Now that you've created a project, try adding team members"
- Never hide features permanently — make them discoverable but not prominent initially

### 5. The Concierge Pattern

A human (or AI-assisted) onboarding experience with personal guidance.

**When to use**: High-ACV products, complex setups, enterprise customers.

**Design rules**:
- Offer scheduling during or immediately after signup
- Send a personalized welcome email from a named person (not a no-reply address)
- Have a clear agenda for the onboarding call
- Follow up with a summary email linking to relevant help docs
- Measure time-to-activation for concierge vs self-serve to determine ROI

## Empty State Design

Empty states are the first thing new users see in each section of your product. They are critical onboarding real estate.

### Empty State Checklist

- [ ] Every empty state has a clear CTA to populate it
- [ ] The CTA explains what the user will get, not just what to do
- [ ] Visual illustration shows what the populated state will look like
- [ ] Empty states never just say "Nothing here yet" — they guide the next action
- [ ] Each empty state reinforces the value of taking the action
- [ ] Copy is encouraging, not clinical

### Empty State Copy Formula

```
[What this section is for — one sentence]
[What you'll be able to do once it's set up — the benefit]
[CTA button: action verb + specific object]
```

Example:
```
"This is where your customer conversations live."
"Connect your email to automatically track and reply to messages — all in one place."
[Connect your email]
```

### Empty State Anti-Patterns

| Anti-Pattern | Why It Fails | Fix |
|---|---|---|
| Blank screen with no guidance | User doesn't know what to do | Add illustration, copy, and CTA |
| "No data found" | Clinical, unhelpful | Explain why and what to do about it |
| Tutorial video in every empty state | Too much passive content | Make it interactive or at least optional |
| CTA that requires many steps | "Import your CSV" is intimidating at first | Start with "Add your first [item] manually" |

## Email Onboarding Sequences

### Sequence Architecture

| Email | Timing | Purpose | Subject Line Pattern |
|---|---|---|---|
| **Welcome** | Immediately | Confirm signup, set expectations, link to first step | "Welcome to [Product] — here's your first step" |
| **Quick win** | Day 1 (4-6 hours later) | Guide to the fastest value moment | "The fastest way to [outcome] with [Product]" |
| **Activation nudge** | Day 2-3 | Re-engage if user hasn't activated | "[Name], you're one step away from [benefit]" |
| **Social proof** | Day 4-5 | Show how others succeeded | "How [Customer] achieved [specific result]" |
| **Feature highlight** | Day 7 | Introduce a complementary feature | "Did you know you can also [feature]?" |
| **Check-in** | Day 10-14 | Personal outreach, offer help | "Need help with [Product]? (reply to this email)" |
| **Trial expiration** | Day 12-13 (if 14-day trial) | Urgency + value recap | "Your trial ends in 2 days — here's what you'll lose" |

### Email Onboarding Rules

1. **Every email must have exactly one CTA**: Do not overwhelm with multiple links and options
2. **Adapt based on behavior**: If the user has already activated, skip the activation nudge emails
3. **Send from a real person**: "Sarah from [Product]" not "The [Product] Team"
4. **Keep emails short**: 100-200 words maximum. Link to resources for detail.
5. **Use behavioral triggers, not just time-based**: "You created a project but haven't added tasks" is more relevant than "It's day 3"
6. **Include a direct reply option**: "Just reply to this email if you're stuck"

### Behavioral vs Time-Based Triggers

| Trigger Type | Example | When to Use |
|---|---|---|
| **Time-based** | "2 days after signup" | Welcome sequence, trial reminders |
| **Action-based** | "After user creates first project" | Feature discovery, next-step guidance |
| **Inaction-based** | "User signed up 3 days ago but hasn't logged in" | Re-engagement, help offers |
| **Milestone-based** | "User has invited 3 team members" | Celebration, upsell opportunity |

Behavioral triggers outperform time-based triggers by 2-3x in click-through rate because they are contextually relevant.

## Activation Metrics

### Primary Metrics

| Metric | Definition | Benchmark (B2B SaaS) |
|---|---|---|
| **Activation rate** | % of signups who complete the activation event | 20-40% (good), 40-60% (excellent) |
| **Time to activate** | Median time from signup to activation event | <1 day (good), <1 hour (excellent) |
| **Day 1 return rate** | % of signups who return on day 2 | 30-50% (good), 50%+ (excellent) |
| **Day 7 return rate** | % of signups who return in the first week | 15-25% (good), 25%+ (excellent) |
| **Setup completion rate** | % who complete all onboarding steps | 30-50% (good), 50%+ (excellent) |

### Diagnostic Metrics

| Metric | What It Reveals |
|---|---|
| Step-by-step completion funnel | Where in onboarding users drop off |
| Time spent per onboarding step | Which steps are confusing or take too long |
| Feature adoption sequence | Which features users discover naturally vs need guidance |
| Support ticket rate (first 7 days) | Gaps in onboarding clarity |
| Onboarding email click-through rate | Which emails drive re-engagement |
| Checklist item completion order | Whether users follow your intended path |

### Cohort Analysis Framework

Compare these cohorts to understand what drives activation:

1. **Activated within 1 day** vs **Activated in 2-7 days** vs **Never activated**
   - What did fast activators do differently?

2. **Organic signups** vs **Paid signups** vs **Referral signups**
   - Do different channels produce different activation rates?

3. **Completed onboarding checklist** vs **Skipped checklist**
   - Does the checklist actually improve outcomes?

4. **Received email sequence** vs **Unsubscribed from emails**
   - Do onboarding emails materially improve activation?

## Time-to-Value Optimization

### The Time-to-Value Audit

Map every step between signup and the aha moment. For each step, measure:

| Step | Time Required | Drop-off Rate | Can It Be Eliminated? | Can It Be Shortened? | Can It Be Deferred? |
|---|---|---|---|---|---|
| Email verification | 30s - 5 min | 10-20% | Yes (verify later) | Yes (magic link) | Yes (allow usage before verification) |
| Profile setup | 1-3 min | 5-15% | Partially (smart defaults) | Yes (reduce fields) | Yes (ask later) |
| Integration setup | 5-15 min | 20-40% | No (if required for value) | Yes (wizard + presets) | Yes (show sample data first) |
| Invite team | 2-5 min | 30-50% | Yes (solo value first) | Yes (share link) | Yes (prompt after activation) |
| First core action | 1-10 min | 10-30% | No (this IS the aha moment) | Yes (templates, AI assist) | No |

### Time-to-Value Reduction Tactics

1. **Eliminate email verification before first use**: Let users in immediately, verify later. This alone can improve activation by 15-25%.
2. **Pre-fill with sample data**: Show users what the product looks like when populated.
3. **Offer templates**: "Start from a template" is faster than "Start from scratch."
4. **Use AI/automation**: Auto-configure based on user profile or stated goal.
5. **Defer non-critical setup**: Anything not needed for the aha moment gets pushed to later.
6. **Reduce perceived time**: Progress bars, step counts, and "this takes 2 minutes" set expectations.

## Onboarding Audit Output Format

When auditing an onboarding flow, deliver:

### 1. Aha Moment Assessment
What is the aha moment? Is it correctly identified? Is the onboarding flow actually pointing toward it?

### 2. Critical Path Map
Step-by-step map from signup to aha moment with time and friction assessment for each step.

### 3. Steps to Eliminate or Defer
Specific steps that can be removed from the critical path without blocking value delivery.

### 4. Empty State Review
Assessment of every empty state the user encounters before activation.

### 5. Email Sequence Review
Evaluation of onboarding emails — timing, copy, CTAs, behavioral targeting.

### 6. Measurement Plan
Metrics to track, cohorts to compare, and targets to aim for.

### 7. Quick Wins
Changes implementable in under a week that will measurably improve activation rate.

## Related Skills
- [signup-flow-cro](../signup-flow-cro/SKILL.md) — Optimize the signup flow that precedes onboarding
- [paywall-upgrade-cro](../paywall-upgrade-cro/SKILL.md) — Convert activated free users to paid
- [page-cro](../page-cro/SKILL.md) — Optimize pages that drive signups into the onboarding funnel
- [ab-test-setup](../ab-test-setup/SKILL.md) — Test onboarding variations rigorously
