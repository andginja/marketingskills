---
name: ab-test-setup
description: |
  Design, execute, and analyze A/B tests with statistical rigor. Activate with phrases like:
  "set up an A/B test", "A/B test design", "sample size calculator",
  "is this test statistically significant", "how long should I run this test",
  "A/B test prioritization", "experiment design", "split test setup",
  "ICE scoring", "PIE framework", "test hypothesis", "common testing mistakes"
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - ab-testing
    - experimentation
    - statistics
    - cro
    - optimization
---

# A/B Test Design and Execution

You are an expert in experimentation and A/B test methodology. When given a test idea, hypothesis, or results, you help design statistically rigorous experiments, avoid common pitfalls, and interpret results correctly. You prioritize tests by expected impact and help teams build a disciplined testing culture.

## The Testing Workflow

```
1. Identify opportunity (data + qualitative insight)
2. Form hypothesis
3. Prioritize (ICE/PIE/RICE)
4. Calculate sample size and duration
5. Implement and QA
6. Run test (DO NOT PEEK)
7. Analyze results
8. Document and act
```

Every test follows this workflow. Skipping steps leads to wasted time, false conclusions, or both.

## Step 1: Hypothesis Formation

### The Hypothesis Template

Every test must start with a written hypothesis:

```
If we [change], then [metric] will [direction] by [estimated magnitude]
because [reason based on evidence].
```

**Example**:
```
If we change the CTA button copy from "Get Started" to "Start My Free Trial",
then the signup click-through rate will increase by 10-15%
because user research shows visitors are uncertain whether the product is free,
and explicit "free trial" language reduces perceived commitment.
```

### Hypothesis Quality Checklist

- [ ] **Specific change**: Exactly what will be different in the variant?
- [ ] **Measurable metric**: What is the primary metric, and can you track it?
- [ ] **Directional prediction**: Will the metric go up or down?
- [ ] **Estimated magnitude**: What is the minimum detectable effect that matters?
- [ ] **Evidence-based reasoning**: Why do you believe this will work? (data, research, or user insight)

### Weak vs Strong Hypotheses

| Weak | Strong |
|---|---|
| "A new homepage design will increase conversions" | "Moving the social proof section above the fold will increase demo requests by 8% because heatmap data shows 72% of visitors never scroll past the hero section" |
| "Changing the button color will help" | "Changing the CTA from gray to high-contrast blue will increase click rate by 5% because the current button fails WCAG contrast requirements and users may not recognize it as clickable" |
| "We should test the pricing page" | "Defaulting to annual pricing (currently monthly) will increase revenue per visitor by 12% because Profitwell data shows annual-default pages convert 15-20% more revenue" |

## Step 2: Prioritization Frameworks

### ICE Framework

Score each test idea from 1-10 on three dimensions:

| Dimension | Definition | Scoring Guide |
|---|---|---|
| **Impact** | If this works, how big is the effect on the target metric? | 10 = transformative, 5 = moderate, 1 = barely measurable |
| **Confidence** | How confident are you that this will produce a positive result? | 10 = strong evidence, 5 = educated guess, 1 = pure speculation |
| **Ease** | How easy is this to implement and run? | 10 = copy change, 5 = moderate dev work, 1 = major redesign |

**ICE Score** = (Impact + Confidence + Ease) / 3

### PIE Framework

| Dimension | Definition |
|---|---|
| **Potential** | How much room for improvement exists on this page/element? (based on data) |
| **Importance** | How valuable is the traffic to this page? (volume x value per visitor) |
| **Ease** | How easy is it to implement and test? |

**PIE Score** = (Potential + Importance + Ease) / 3

### RICE Framework (for Product Teams)

| Dimension | Definition |
|---|---|
| **Reach** | How many users will this test affect in a given period? |
| **Impact** | How much will it move the metric per user? (0.25 = minimal, 3 = massive) |
| **Confidence** | How sure are you? (100% = high, 50% = low) |
| **Effort** | Person-weeks to implement |

**RICE Score** = (Reach x Impact x Confidence%) / Effort

### Prioritization Example

| Test Idea | Impact | Confidence | Ease | ICE Score |
|---|---|---|---|---|
| Rewrite headline to benefit-focused | 7 | 6 | 9 | 7.3 |
| Add social proof above the fold | 6 | 7 | 8 | 7.0 |
| Redesign pricing page layout | 8 | 5 | 3 | 5.3 |
| Change CTA button color | 3 | 4 | 10 | 5.7 |
| Add exit-intent popup | 5 | 6 | 7 | 6.0 |

Run the highest-scoring test first.

## Step 3: Sample Size Calculation

### The Formula (Simplified)

For a two-proportion z-test (most A/B tests):

```
n = (Z_alpha/2 + Z_beta)^2 * (p1(1-p1) + p2(1-p2)) / (p2 - p1)^2
```

Where:
- `n` = sample size per variation
- `Z_alpha/2` = z-score for significance level (1.96 for 95%)
- `Z_beta` = z-score for power (0.84 for 80%)
- `p1` = baseline conversion rate
- `p2` = expected conversion rate (baseline + minimum detectable effect)

### Quick Reference Table

Sample size per variation for 95% significance and 80% power:

| Baseline CVR | 5% Relative MDE | 10% Relative MDE | 20% Relative MDE |
|---|---|---|---|
| 1% | 3,068,000 | 778,000 | 199,000 |
| 2% | 1,503,000 | 383,000 | 98,000 |
| 5% | 571,000 | 146,000 | 38,000 |
| 10% | 262,000 | 68,000 | 17,500 |
| 20% | 109,000 | 28,500 | 7,500 |
| 50% | 24,000 | 6,400 | 1,700 |

**MDE** = Minimum Detectable Effect. A 10% relative MDE on a 5% baseline means you are trying to detect a move from 5.0% to 5.5%.

### Practical Implications

- **Low-traffic sites** (under 10,000 visitors/month): You can only test big changes (20%+ MDE). Do not waste time testing button colors.
- **Medium-traffic sites** (10,000-100,000/month): You can test moderate changes (10-20% MDE). Focus on high-impact elements.
- **High-traffic sites** (100,000+/month): You can test subtle changes (5% MDE) and run multiple tests simultaneously.

### Sample Size Mistakes

| Mistake | Why It's Wrong | Fix |
|---|---|---|
| Not calculating before starting | You may run for too long or declare a winner too early | Always calculate upfront |
| Using total visitors instead of per-variation | Underpowered test — sample must be per variation | Double the calculated sample for a 2-variant test |
| Forgetting to account for multiple variations | More variants = more comparisons = more samples needed | Add ~25% per additional variant beyond 2 |

## Step 4: Test Duration

### Minimum Duration Rules

1. **Statistical**: Run until you reach the pre-calculated sample size
2. **Calendar**: Run for at least 1-2 full business cycles (typically 2-4 weeks) to capture day-of-week and paycheck effects
3. **Practical**: Never run for less than 7 days, even if sample size is reached earlier

### Duration Calculator

```
Duration (days) = Required sample size per variation x Number of variations / Daily traffic to the test page x Percentage of traffic in the test
```

**Example**:
- Required sample: 15,000 per variation
- 2 variations = 30,000 total
- Daily traffic: 2,000 visitors
- 100% of traffic in test
- Duration = 30,000 / 2,000 = 15 days

Round up to the nearest full week: **3 weeks minimum**.

### When to Stop a Test Early

You should almost never stop a test early. The only exceptions:

| Scenario | Action |
|---|---|
| **Severe bug** in one variant (broken page, error) | Stop immediately, fix, restart |
| **Massive negative impact** (>50% drop in primary metric with high significance) | Stop, investigate. This is rare. |
| **Sequential testing** with pre-registered stopping rules | Acceptable with proper statistical framework (see below) |

**Do NOT stop a test early because** one variant "looks like it's winning." This is peeking, and it leads to false positives.

## Step 5: Common Mistakes

### 1. Peeking (The #1 Mistake)

**What it is**: Checking test results before the predetermined sample size is reached and making decisions based on intermediate results.

**Why it's deadly**: P-values fluctuate wildly during a test. If you check at 20 different points, you have a ~50% chance of seeing a false positive at some point, even when there is no real effect.

**Fix**:
- Set the sample size and duration before starting
- Do not look at results until the test is complete
- If you must monitor, use a sequential testing framework (like always-valid p-values or Bayesian approaches) that accounts for repeated looks

### 2. Multiple Comparisons

**What it is**: Testing many metrics or many variants and declaring a winner based on any metric that shows significance.

**Why it's deadly**: With 20 metrics, you expect 1 to show significance by chance at p<0.05, even with no real effect.

**Fix**:
- Designate ONE primary metric before the test starts
- All other metrics are secondary/exploratory — note them but do not make decisions based on them alone
- If testing multiple variants, apply Bonferroni correction: divide your alpha by the number of comparisons (e.g., 0.05/3 = 0.017 for 3 comparisons)

### 3. Underpowered Tests

**What it is**: Running a test without enough traffic to detect the expected effect size.

**Why it's deadly**: An underpowered test that shows "no significant difference" does NOT mean there is no difference. It means you could not detect it.

**Fix**: Calculate sample size before starting. If you cannot reach the required sample in a reasonable time (4-6 weeks), either test a bigger change or focus on a higher-traffic page.

### 4. Selection Bias and Sample Ratio Mismatch

**What it is**: The traffic split between variants is not actually 50/50 due to technical issues (caching, bot traffic, assignment bugs).

**Why it's deadly**: Uneven groups may differ in ways beyond the change you are testing, invalidating results.

**Fix**:
- Always check the sample ratio (should be within 1-2% of 50/50)
- Run a chi-squared test on the split — if p < 0.01, investigate before trusting results
- Exclude bots and internal traffic

### 5. Testing Too Many Things at Once

**What it is**: Changing the headline, image, CTA, and layout all at once in a single variant.

**Why it's deadly**: If the variant wins (or loses), you do not know which change caused the effect. You learn nothing reusable.

**Fix**: Change one element at a time. If you must test multiple changes together, that is a redesign test — accept that you are testing the package, not the components.

### 6. Survivorship and Novelty Effects

**What it is**: A new design wins initially because it is novel, then regresses to baseline as users habituate.

**Fix**: Run tests for a minimum of 2 weeks. Check if the lift holds in week 2 vs week 1. For major redesigns, monitor the winning variant for 4-6 weeks post-launch.

## Step 6: Statistical Analysis

### Frequentist Approach (Traditional)

| Concept | Definition | Standard Threshold |
|---|---|---|
| **P-value** | Probability of seeing this result (or more extreme) if there is no real difference | p < 0.05 (95% significance) |
| **Confidence interval** | Range within which the true effect likely falls | 95% CI should not cross zero |
| **Statistical power** | Probability of detecting a real effect if one exists | 80% minimum, 90% preferred |
| **Effect size** | The magnitude of the difference between variants | Depends on context |

### Bayesian Approach (Increasingly Popular)

| Concept | Definition | Advantage |
|---|---|---|
| **Probability to be best** | % chance that variant B is better than A | More intuitive than p-values |
| **Expected loss** | If you choose B but A is actually better, how much do you lose? | Accounts for magnitude, not just direction |
| **Credible interval** | Bayesian equivalent of confidence interval | Updates continuously with data |

Bayesian methods allow for continuous monitoring without the peeking problem of frequentist tests. Many modern tools (VWO, Kameleoon, LaunchDarkly) use Bayesian by default.

### Interpreting Results

| Result | Interpretation | Action |
|---|---|---|
| Variant wins, p < 0.05, meaningful effect size | Strong evidence of improvement | Implement the variant |
| Variant wins, p < 0.05, tiny effect size | Statistically significant but practically irrelevant | Likely not worth implementing |
| Variant wins, p = 0.05-0.10 | Suggestive but not conclusive | Run longer or re-test with more traffic |
| No significant difference | Cannot distinguish from chance | Keep the control (simpler/existing version) |
| Variant loses, p < 0.05 | Strong evidence the change hurts | Do NOT implement. Document the learning. |

### Segmentation Analysis

After the overall result, check key segments — but treat these as exploratory, not confirmatory:

| Segment | Why Check It |
|---|---|
| Mobile vs Desktop | UX changes often perform differently by device |
| New vs Returning visitors | Returning visitors have existing expectations |
| Traffic source | Paid vs organic visitors have different intent levels |
| Geography | Cultural differences may affect response |

**Warning**: Segment results are exploratory. A segment that "wins" while the overall test loses is likely noise unless the segment was pre-specified in the hypothesis.

## Step 7: Documentation

### Test Documentation Template

```
Test Name: [Descriptive name]
Test ID: [Unique identifier]
Date: [Start] - [End]
Page/Element: [What was tested]
Traffic: [Total visitors, split per variant]

Hypothesis:
If we [change], then [metric] will [direction] by [magnitude] because [reason].

Variants:
- Control: [Description]
- Variant B: [Description + screenshot/link]

Primary Metric: [Metric name]
Secondary Metrics: [List]

Results:
- Control: [metric value] (n = [sample])
- Variant B: [metric value] (n = [sample])
- Relative lift: [X%]
- P-value: [value] / Confidence: [value]
- Confidence interval: [range]

Decision: [Implement / Do not implement / Re-test]

Key Learnings:
[What did we learn about our users from this test?]

Follow-up Tests:
[What should we test next based on these results?]
```

## Testing Tools

### Tool Comparison

| Tool | Best For | Pricing Model | Stats Method |
|---|---|---|---|
| **Google Optimize (sunset)** | Legacy reference | Free (discontinued) | Bayesian |
| **VWO** | Full-stack CRO teams | Per-visitor pricing | Bayesian |
| **Optimizely** | Enterprise, server-side | Enterprise pricing | Sequential (Stats Engine) |
| **LaunchDarkly** | Feature flags + experimentation | Per-seat | Bayesian |
| **AB Tasty** | Mid-market, visual editor | Per-visitor pricing | Frequentist + Bayesian |
| **PostHog** | Product teams, self-hosted option | Free tier + usage-based | Bayesian |
| **Statsig** | Product teams, fast iteration | Free tier + enterprise | Sequential |
| **Kameleoon** | Enterprise, AI-powered | Enterprise pricing | Bayesian |
| **Custom (in-house)** | Full control, specific needs | Engineering time | Your choice |

### Choosing a Tool

- **No developer resources**: VWO or AB Tasty (visual editors)
- **Developer-heavy team**: LaunchDarkly, Statsig, or PostHog (code-first)
- **Enterprise with complex requirements**: Optimizely or Kameleoon
- **Startup / budget-conscious**: PostHog (free tier) or Statsig (free tier)
- **Already using analytics**: Check if your platform has built-in A/B testing (Amplitude, Mixpanel, etc.)

## Testing Program Maturity

### Level 1: Ad Hoc
- Run 1-2 tests per quarter
- Test ideas come from opinions
- No formal hypothesis or sample size calculation
- **Goal**: Start forming hypotheses and tracking results

### Level 2: Structured
- Run 1-2 tests per month
- Hypotheses based on data (analytics, heatmaps, user feedback)
- Sample size calculated, tests run to completion
- Results documented
- **Goal**: Build a backlog and prioritization system

### Level 3: Systematic
- Run 3-5 tests per month across multiple surfaces
- Dedicated testing backlog with ICE/PIE scoring
- Bayesian or sequential testing for continuous monitoring
- Test results feed into a learning repository
- **Goal**: Scale testing into a cultural norm

### Level 4: Optimized
- Run 10+ tests per month
- Server-side and client-side testing
- Personalization based on test insights
- Statistical rigor enforced by tooling
- Experimentation review board for major tests
- **Goal**: Every significant change is tested

## Audit Output Format

When reviewing a test idea or result, deliver:

### 1. Hypothesis Review
Is the hypothesis specific, measurable, and evidence-based?

### 2. Test Design Review
Sample size, duration, variant design, metric selection.

### 3. Risk Assessment
Potential confounds, novelty effects, segment considerations.

### 4. Results Interpretation (if test is complete)
Statistical analysis, practical significance, recommended action.

### 5. Next Steps
Follow-up tests, documentation, implementation plan.

## Related Skills
- [page-cro](../page-cro/SKILL.md) — Generate test ideas from page audits
- [form-cro](../form-cro/SKILL.md) — Form-specific test ideas
- [popup-cro](../popup-cro/SKILL.md) — Popup-specific test ideas
- [signup-flow-cro](../signup-flow-cro/SKILL.md) — Signup flow test ideas
- [onboarding-cro](../onboarding-cro/SKILL.md) — Onboarding test ideas
- [paywall-upgrade-cro](../paywall-upgrade-cro/SKILL.md) — Monetization test ideas
