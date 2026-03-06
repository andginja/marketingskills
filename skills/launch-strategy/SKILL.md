---
name: launch-strategy
description: |
  Product launch playbook and execution framework. Use when the user asks about:
  - launching a product or feature
  - product launch strategy or checklist
  - launch plan or launch playbook
  - pre-launch preparation
  - launch day execution
  - post-launch momentum
  - feature announcement strategy
  - ORB framework or launch channels
  - early access or beta launch
metadata:
  version: 1.0.0
  author: Andre Ginja
  tags:
    - product-launch
    - go-to-market
    - feature-release
---

# Product Launch Strategy

## The ORB Channel Framework

Every launch should distribute across three channel types. Relying on only one is the most common launch failure mode.

### Owned Channels
Channels you control completely. These are your foundation.

- **Email list** — Your highest-converting channel. Segment by engagement level and customer stage. Send a sequence, not a single blast: teaser (7 days out), announcement (launch day), follow-up (day 2), last chance (day 5).
- **Blog / website** — Publish a launch post that serves double duty as evergreen SEO content. Include the problem, solution, social proof, and a clear CTA.
- **In-app messaging** — For existing products, notify current users contextually. Use banners, modals, or tooltips depending on the significance of the launch.
- **Social media profiles** — Your company and founder accounts. Organic reach is limited, so pair with engagement tactics (polls, threads, behind-the-scenes content).
- **Community** — Slack, Discord, or forum communities you manage. These are your most engaged users.
- **Podcast / YouTube** — If you have an existing audience here, a dedicated launch episode or video is high-impact.

### Rented Channels
Channels where you pay for distribution. Use these to amplify beyond your existing audience.

- **Paid social ads** — Retarget website visitors and lookalike audiences during launch week. Budget heavier on days 1-3.
- **Sponsored newsletters** — Book placements 4-6 weeks in advance. Match the newsletter audience to your ICP.
- **Influencer partnerships** — Identify 5-10 creators whose audience overlaps with your target market. Provide early access and a clear brief, not a script.
- **Product Hunt / launch platforms** — Treat as an amplifier, not a strategy. Coordinate your community to support on launch day.
- **PPC / search ads** — Bid on competitor and category keywords during launch to capture intent.

### Borrowed Channels
Channels you access through relationships and goodwill. Often the highest ROI but require advance investment.

- **Press / media coverage** — Pitch a story, not a product. Journalists care about trends, data, and human interest. Embargo your news to give exclusive access.
- **Partner co-marketing** — Identify non-competitive companies with overlapping audiences. Propose mutual promotion.
- **Guest content** — Write for publications your audience reads. Tie to the launch narrative without being overtly promotional.
- **Customer advocacy** — Arm your best customers with shareable content. Make it easy for them to spread the word.
- **Industry communities** — Hacker News, Reddit, indie hacker forums, Slack groups. Contribute genuinely; do not spam.

## The 5-Phase Launch Model

### Phase 1: Internal Launch (T-30 days)
**Goal:** Align the entire company around the launch narrative.

- Write the press release before building (Amazon's "Working Backwards" method). This forces clarity on the value proposition.
- Create an internal launch brief covering: what is launching, who it is for, why it matters, key messages, competitive positioning, and success metrics.
- Brief all teams: sales needs talk tracks, support needs documentation, success needs onboarding flows.
- Record a 5-minute internal demo video so every employee can articulate the product.
- Define launch tier (Tier 1 = major product, Tier 2 = significant feature, Tier 3 = minor update) to calibrate effort.

### Phase 2: Alpha Launch (T-21 days)
**Goal:** Validate with a small group of trusted users. Find critical bugs and messaging gaps.

- Select 10-20 users who represent your ICP and have a relationship with your team.
- Provide a structured feedback framework: What did you expect? What surprised you? What would you tell a friend about this?
- Iterate on both the product and the messaging based on feedback.
- Collect 3-5 testimonials or quotes you can use at launch.
- Identify the "aha moment" — the specific action or screen where users get excited. Build your launch narrative around this.

### Phase 3: Beta Launch (T-14 days)
**Goal:** Expand to a larger group. Stress-test infrastructure and support processes.

- Open to 50-200 users via a waitlist or application process.
- Monitor usage analytics closely: activation rate, feature adoption, drop-off points.
- Run your support playbook in production. Identify the top 5 questions and pre-write help docs.
- A/B test your landing page headline and CTA with this cohort's traffic.
- Begin seeding social proof: case studies, usage stats, user-generated content.

### Phase 4: Early Access (T-7 days)
**Goal:** Build anticipation and capture demand before the public launch.

- Open a waitlist with a viral mechanic (move up the list by sharing).
- Send the teaser email to your full list. Focus on the problem, hint at the solution.
- Brief press contacts under embargo. Provide assets (screenshots, founder quotes, data points).
- Schedule all social media content for launch week.
- Do a full dry run of launch day: test every link, every redirect, every signup flow.

### Phase 5: Full Launch (Launch Day + 14 days)
**Goal:** Maximize reach and convert attention into users and revenue.

- Launch day is the beginning, not the end. Plan for a 2-week launch window.
- Day 1: Publish everywhere simultaneously. Coordinate your ORB channels.
- Days 2-3: Engage with every comment, share, and mention. Responsiveness during this window drives algorithmic amplification.
- Days 4-7: Publish follow-up content — a "behind the scenes" post, usage data, customer story.
- Days 8-14: Retarget engaged-but-unconverted visitors. Send the "last chance" email for any launch pricing.

## Pre-Launch Checklist

### Product Readiness
- [ ] Core feature set complete and tested
- [ ] Onboarding flow optimized (< 2 minutes to value)
- [ ] Error handling and edge cases covered
- [ ] Performance tested under expected load (3x your optimistic estimate)
- [ ] Analytics and event tracking implemented
- [ ] Billing and payment flow tested end-to-end

### Marketing Readiness
- [ ] Landing page live with clear value prop, social proof, and CTA
- [ ] Email sequences drafted and scheduled (teaser, announcement, follow-up, last chance)
- [ ] Social media content created for 14 days
- [ ] Press kit assembled (logos, screenshots, founder bio, key stats, boilerplate)
- [ ] Blog post / announcement written
- [ ] Video demo or walkthrough produced
- [ ] Comparison / alternatives content published for SEO

### Sales and Support Readiness
- [ ] Sales talk track and one-pager created
- [ ] Help documentation published
- [ ] FAQ covering top 10 expected questions
- [ ] Support team briefed and staffed for launch week
- [ ] Escalation paths defined for critical issues

### Technical Readiness
- [ ] Monitoring and alerting configured
- [ ] Rollback plan documented
- [ ] CDN and caching verified
- [ ] SSL certificates valid
- [ ] Redirect chains tested
- [ ] OG tags and social sharing previews verified

## Launch Day Execution

### Hour-by-Hour Playbook

**T-1 hour:**
- Final check on all systems, links, and landing pages.
- Confirm all team members are online and in the war room channel.
- Pre-stage all social posts for rapid publishing.

**T-0 (Launch):**
- Publish the blog post and update the landing page.
- Send the announcement email.
- Post on all social channels within a 30-minute window.
- Submit to Product Hunt, Hacker News, or relevant platforms.
- Notify partners and press that the embargo is lifted.

**T+1 to T+4 hours:**
- Monitor analytics in real-time: traffic, signups, errors.
- Respond to every social media mention and comment within 15 minutes.
- Watch for support tickets and escalate patterns quickly.
- Share early traction internally to maintain energy.

**T+8 hours:**
- First debrief: What is working? What needs adjustment?
- Double down on the channel driving the most conversions.
- Fix any broken flows or unexpected issues.

**T+24 hours:**
- Send a day-1 recap to the team with key metrics.
- Publish a "thank you" or "what we learned" social post.
- Begin the follow-up email sequence for non-converters.

## Post-Launch Momentum

The biggest mistake is treating launch day as the finish line. Most successful products sustain momentum for 4-8 weeks post-launch.

### Week 1-2: Amplification
- Publish customer stories and early results.
- Share behind-the-scenes content about the build process.
- Run a live demo or AMA session.
- Engage in every relevant community discussion.

### Week 3-4: Deepening
- Publish a detailed "lessons learned" or "first 1000 users" post.
- Release a feature comparison guide targeting competitor keywords.
- Launch a referral or incentive program to drive word-of-mouth.
- Collect and publish NPS or satisfaction data.

### Week 5-8: Sustained Growth
- Transition from launch mode to growth mode.
- Set up evergreen content and SEO plays around the product category.
- Build the retargeting funnel for long-tail conversions.
- Plan the next feature launch to maintain cadence.

## Feature Announcement Templates

### Minor Feature (Tier 3)
- In-app tooltip or banner notification
- Changelog entry
- Brief social media post
- Mention in the next newsletter

### Significant Feature (Tier 2)
- Dedicated blog post with use cases
- Email to relevant user segments
- Social media thread with visuals
- In-app announcement with CTA to try it
- Update to help documentation

### Major Launch (Tier 1)
- Full ORB channel activation
- 5-phase launch process
- Press outreach and partner coordination
- Dedicated landing page
- Video content and demos
- Launch event or webinar

## Launch Metrics Framework

### Leading Indicators (Track During Launch)
- **Traffic:** Unique visitors to launch page, traffic sources, referral breakdown
- **Engagement:** Time on page, scroll depth, video play rate
- **Conversion:** Signup rate, trial starts, demo requests
- **Virality:** Social shares, referral signups, organic mentions
- **Sentiment:** Social media sentiment, support ticket tone, NPS

### Lagging Indicators (Track Post-Launch)
- **Activation:** Percentage of signups who reach the "aha moment"
- **Retention:** Day 1, day 7, day 30 return rates
- **Revenue:** New MRR, expansion revenue, average deal size
- **Efficiency:** Customer acquisition cost (CAC) by channel
- **Word-of-mouth:** Organic search growth, direct traffic growth, referral rate

### Benchmarks for SaaS Launches
- Landing page conversion rate: 3-8% (cold traffic), 15-30% (warm traffic)
- Email announcement open rate: 30-50%
- Email announcement click rate: 5-15%
- Free trial to paid conversion: 10-25%
- Day 1 activation rate target: 40-60%

## Common Launch Failures and How to Avoid Them

1. **Single-channel dependency** — Diversify across ORB. If Product Hunt is your only plan, you do not have a plan.
2. **No pre-launch audience** — Start building your email list and community 3-6 months before launch.
3. **Premature optimization** — Do not spend weeks perfecting your landing page if you have no traffic strategy.
4. **Launch and forget** — Plan for 4-8 weeks of sustained post-launch activity.
5. **Internal misalignment** — If sales is surprised by the launch, you skipped Phase 1.
6. **No clear CTA** — Every piece of launch content needs one specific action you want the reader to take.
7. **Ignoring feedback loops** — Monitor support tickets and social mentions obsessively during launch week. They contain your roadmap.
