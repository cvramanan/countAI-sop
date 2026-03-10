# LeadPulze — Product Release SOP

**Version:** 2.0 | **Last updated:** March 2026 | **Owner:** Product Team  
**Applies to:** Engineering · Product · QA · Marketing · Sales

> **Purpose:** Ensure every feature release at LeadPulze is safe, predictable, and well communicated. If you are shipping anything — read this first.

---

## Table of Contents

| # | Section |
|---|---------|
| [01](#01--release-philosophy) | Release Philosophy |
| [02](#02--release-cadence) | Release Cadence |
| [03](#03--roles--responsibilities) | Roles & Responsibilities |
| [04](#04--core-tools) | Core Tools |
| [05](#05--definition-of-done) | Definition of Done |
| [06](#06--git-workflow) | Git Workflow |
| [07](#07--versioning-semver) | Versioning (SemVer) |
| [08](#08--feature-flag-strategy) | Feature Flag Strategy |
| [09](#09--release-documentation-template) | Release Documentation Template |
| [10](#10--qa-testing-process) | QA Testing Process |
| [11](#11--deployment-process) | Deployment Process |
| [12](#12--smoke-test-checklist) | Smoke Test Checklist |
| [13](#13--rollback-procedure) | Rollback Procedure |
| [14](#14--production-incident-protocol) | Production Incident Protocol |
| [15](#15--communication-strategy) | Communication Strategy |
| [16](#16--release-communication-flow) | Release Communication Flow |
| [17](#17--email-announcement) | Email Announcement |
| [18](#18--mobile-push-notification) | Mobile Push Notification |
| [19](#19--in-app-pop-up) | In-App Pop-up |
| [20](#20--public-changelog) | Public Changelog |
| [21](#21--social-media) | Social Media |
| [22](#22--sales-enablement-pack) | Sales Enablement Pack |
| [23](#23--feature-adoption-monitoring) | Feature Adoption Monitoring |
| [24](#24--customer-feedback-collection) | Customer Feedback Collection |
| [25](#25--post-release-review) | Post-Release Review |
| [→](#master-release-flow) | Master Release Flow |

---

## 01 — Release Philosophy

Every release follows this lifecycle:

```
Build → Validate → Deploy → Announce → Learn
```

### Core Principles

| Principle | What it means in practice |
|-----------|--------------------------|
| **Never break production** | Every feature ships behind a flag. Staging is tested before production. |
| **Always be able to rollback** | Every release has a documented rollback plan before it ships. |
| **Every release has a success metric** | If you can't measure it, you can't call it a success. |
| **Communication after stability** | No announcements until the smoke test has passed. |

---

## 02 — Release Cadence

LeadPulze uses **Continuous Deployment with Structured Communication** — engineers can deploy anytime, but user-facing releases follow a weekly rhythm.

| Activity | Frequency |
|----------|-----------|
| Engineering deploys | Anytime (behind feature flags) |
| User-visible releases | Weekly |
| Major announcements | Monthly |

### Recommended Weekly Schedule

| Day | Activity |
|-----|----------|
| Monday – Wednesday | Development & code review |
| Thursday | Release window — deploy to production |
| Friday | Monitoring & early feedback |

> Hotfixes and critical patches can ship outside this window. All other releases should wait for Thursday unless there is a business-critical reason.

---

## 03 — Roles & Responsibilities

Every task has one accountable owner. If a task has no owner, it will not get done.

| Role | Responsibilities |
|------|-----------------|
| **Engineer** | Feature development, PR creation, branch management |
| **Engineering Lead** | Code review, version tagging, deployment oversight |
| **QA Lead** | Testing sign-off on staging and production smoke test |
| **Product Manager** | Release planning, documentation, internal briefing, go/no-go decision |
| **DevOps / Backend Engineer** | Staging and production deployment, infrastructure monitoring |
| **Product Marketing** | Demo video, email, push notification, social posts, changelog |
| **Customer Success** | Customer feedback collection, post-release interviews |

---

## 04 — Core Tools

One tool per category. Do not introduce new tools without team agreement.

| Category | Tool | Purpose |
|----------|------|---------|
| **Code repository** | GitHub | Source control, PRs, version tags |
| **CI/CD** | GitHub Actions | Automated tests, builds, and deploys |
| **Internal documentation** | Notion | Release docs, SOPs, internal FAQs |
| **Product analytics** | PostHog | Feature usage tracking and events |
| **Error monitoring** | Datadog | Real-time errors and performance alerts |
| **Feature flags** | LaunchDarkly | Controlled feature rollouts and instant rollback |
| **Product email** | Resend | Transactional and marketing emails |
| **Demo videos** | Loom | Quick feature walkthroughs |

> **Rule: 1 category = 1 tool.** Using multiple tools for the same job creates confusion and gaps in visibility.

---

## 05 — Definition of Done

A feature is only ready to ship when every item below is complete. The Product Manager verifies this before the deploy is approved.

### Code

- [ ] Feature implemented on a feature branch
- [ ] Code reviewed and approved (minimum 1 reviewer)
- [ ] All CI tests passing
- [ ] No direct commits to `main`

### Quality

- [ ] QA Lead has signed off
- [ ] Edge cases tested
- [ ] Mobile responsiveness verified
- [ ] Error states handled

### Technical

- [ ] Analytics events added and verified in PostHog
- [ ] Feature flag created in LaunchDarkly
- [ ] Database migrations tested (if applicable)

### Documentation & Planning

- [ ] Release document completed in Notion
- [ ] Rollback plan defined and documented
- [ ] Sales enablement pack ready (major features only)
- [ ] Internal teams briefed

> ⚠️ **If any item is unchecked → feature cannot ship.**

---

## 06 — Git Workflow

### Branch Naming

```
feature/<feature-name>     →  new functionality
fix/<bug-name>             →  non-critical bug fixes
hotfix/<critical-fix>      →  critical production fixes
```

**Examples:**

```
feature/auto-followup
feature/sales-reporting
fix/contact-import
hotfix/auth-token-expiry
```

### Step-by-Step

**1. Create your feature branch**

```bash
git checkout main
git pull origin main
git checkout -b feature/auto-followup
```

**2. Write and commit your changes**

Use [Conventional Commits](https://www.conventionalcommits.org/) format:

```bash
git add .
git commit -m "feat: add auto follow-up scheduling"

# Other prefixes:
# fix:      bug fixes
# perf:     performance improvements
# refactor: code restructuring
# docs:     documentation changes
# test:     adding tests
# chore:    maintenance tasks
```

**3. Push your branch**

```bash
git push origin feature/auto-followup
```

**4. Open a Pull Request on GitHub**

Every PR must:

- [ ] Pass all CI checks
- [ ] Have at least 1 approval from another engineer
- [ ] Include a clear description of what changed and why
- [ ] Include screenshots or a Loom link (if UI changes)
- [ ] Link to the relevant Notion release doc or Linear/Jira ticket

> ❌ No direct commits to `main`. No self-merges without approval.

---

## 07 — Versioning (SemVer)

Every release must be tagged before it ships. We follow [Semantic Versioning](https://semver.org/).

### Format

```
MAJOR.MINOR.PATCH
```

| Type | When to increment | Example |
|------|-------------------|---------|
| **MAJOR** | Breaking change — existing users or integrations are affected | `v1.0.0` → `v2.0.0` |
| **MINOR** | New feature — backwards-compatible, nothing breaks | `v1.2.0` → `v1.3.0` |
| **PATCH** | Bug fix or small improvement — no new functionality | `v1.3.0` → `v1.3.1` |

### Tagging a Release

```bash
git checkout main
git pull origin main
git tag v1.3.0
git push origin v1.3.0
```

---

## 08 — Feature Flag Strategy

**All new features must ship behind a feature flag. No exceptions.**

A flag lets us turn a feature on/off instantly without redeploying code. This is our primary safety net.

### Naming Convention

Use lowercase with underscores. Always prefix with `feature_`.

```
feature_auto_followup
feature_sales_reporting
feature_pipeline_analytics
```

### Rollout Stages

Always progress through stages in order. Do not jump straight to 100%.

| Stage | Who has access | Purpose |
|-------|----------------|---------|
| **Internal** | LeadPulze team only | Verify everything works in production before users see it |
| **Beta** | Selected users (opt-in or invited) | Gather early feedback, catch edge cases |
| **25% rollout** | 1 in 4 users | Gradual exposure — monitor for errors before full release |
| **100% rollout** | All users | Full release — confident in stability |

### If Something Goes Wrong

**Disable the feature flag immediately.** This hides the feature for all users in seconds, without a code deploy. Then follow the [Rollback Procedure](#13--rollback-procedure).

---

## 09 — Release Documentation Template

Every release requires a completed Release Document in Notion before the deploy is approved. The Product Manager owns this.

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LEADPULZE — RELEASE DOCUMENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Feature Name:
Version:
Release Date:
Product Manager:
Engineer:

────────────────────────────────────────────
OVERVIEW
────────────────────────────────────────────
Problem Solved:
  What user or business problem does this solve?

What's New:
  What changed or was added?

Who Benefits:
  Which users or segments does this affect?

────────────────────────────────────────────
USAGE
────────────────────────────────────────────
How to Use:
  Brief instructions or link to help docs.

Known Limitations:
  Edge cases, missing functionality, or intentional out-of-scope items.

────────────────────────────────────────────
TECHNICAL
────────────────────────────────────────────
Feature Flag Name:
  e.g. feature_auto_followup

Rollout Status:
  [ ] Internal   [ ] Beta   [ ] 25% rollout   [ ] 100% rollout

Rollback Plan:
  Step-by-step: what to do if something goes wrong after deploy.

────────────────────────────────────────────
SUCCESS
────────────────────────────────────────────
Success Metric:
  What does good look like? (e.g. "40% of users activate within 7 days")

PostHog Dashboard:
  Link to the feature analytics dashboard.

Datadog Monitor:
  Link to the error/performance monitor for this feature.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 10 — QA Testing Process

QA Lead owns the sign-off. No feature ships without it.

### Functional Testing

- [ ] Feature works end-to-end in the happy path
- [ ] Edge cases handled (empty states, invalid input, large data sets)
- [ ] Error states display correctly and recover gracefully

### Integration Testing

- [ ] API responses are correct and match expected schema
- [ ] Database migrations run cleanly and are reversible
- [ ] Feature flag behaviour is verified (on and off states both work)

### UX Testing

- [ ] Mobile responsiveness (iOS and Android)
- [ ] All UI interactions work as designed
- [ ] Loading and empty states are present
- [ ] No broken layouts at standard screen sizes (1280px, 1440px, mobile)

### Analytics Validation

- [ ] PostHog events are firing for all key user actions
- [ ] Events appear in the PostHog dashboard with correct properties
- [ ] No duplicate or missing events

> QA testing happens on **staging** with the feature flag **enabled**. If staging tests fail, the feature does not proceed to production.

---

## 11 — Deployment Process

DevOps owns the deploy. Product Manager gives the final go/no-go.

```
1.  Merge PR to main
          ↓
2.  GitHub Actions runs automated tests
          ↓
3.  Deploy to staging
          ↓
4.  QA tests staging (feature flag enabled)
          ↓
5.  QA Lead signs off
          ↓
6.  Product Manager gives go/no-go
          ↓
7.  Enable feature flag → Internal stage
          ↓
8.  Deploy to production
          ↓
9.  Verify Datadog monitoring is active
          ↓
10. Smoke test (must complete within 10 minutes)
          ↓
11. PM confirms production is stable
          ↓
12. Begin communication sequence (see §16)
```

> If the smoke test fails at step 10 → go to [§13 Rollback Procedure](#13--rollback-procedure) immediately. Do not send any communications until production is re-confirmed stable.

---

## 12 — Smoke Test Checklist

Run immediately after every production deploy. Must complete within **10 minutes**.

| Check | What to verify |
|-------|---------------|
| ☐ Login | Can a user log in successfully? |
| ☐ Lead creation | Can a new lead be created? |
| ☐ Core product flow | Does the primary user journey work end-to-end? |
| ☐ New feature accessible | Is the new feature visible and functional (with flag enabled)? |
| ☐ No critical errors | Are there any P1 or P2 errors in Datadog? |

> If any check fails → disable the feature flag and follow the Rollback Procedure.

---

## 13 — Rollback Procedure

Follow these steps if a serious issue is detected after production deploy.

### Step 1 — Contain Immediately

```
Disable the feature flag in LaunchDarkly.
→ Feature is hidden for all users instantly, no redeploy needed.
```

### Step 2 — Notify the Team

```
Post in #releases on Slack:
  - What broke
  - When it was detected
  - What action has been taken so far

Tag: Engineering Lead + Product Manager
```

### Step 3 — Assess

```
Engineering Lead checks Datadog:
  - Scope of impact (how many users affected?)
  - Is the flag disable sufficient, or is a code rollback needed?
```

### Step 4 — Code Rollback (if needed)

```bash
git revert <merge-commit-hash>
git push origin main
# GitHub Actions re-runs and redeploys
```

### Step 5 — Database Rollback (if needed)

```
Run the down migration:
  - Confirm with Engineering Lead before executing
  - Verify data integrity after rollback
```

### Step 6 — Verify Stability

```
Re-run smoke test checklist (§12).
Confirm no errors in Datadog.
PM confirms production is stable.
```

### Step 7 — Post-Incident

```
Within 48 hours:
  - Write a brief incident summary (what broke, why, how long, how fixed)
  - Add summary to the release doc in Notion
  - Log a ticket for the root cause fix
  - Schedule a post-mortem if it was a P1 incident
  - Do not re-enable the flag until root cause is fixed and re-tested on staging
```

---

## 14 — Production Incident Protocol

Incidents are classified by severity. The Engineering Lead is the incident owner.

| Severity | Description | Immediate Action | Comms |
|----------|-------------|-----------------|-------|
| **P1** | System unusable — login broken, data loss, full outage | Immediate rollback | Notify team in <15 min, status update every 30 min |
| **P2** | Feature broken — core flow impaired but system usable | Disable feature flag | Notify team, fix in current deploy cycle |
| **P3** | Minor bug — cosmetic or edge case, low user impact | Log ticket | Fix in next scheduled deploy |

> P1 incidents require a post-mortem regardless of how quickly they were resolved.

---

## 15 — Communication Strategy

Not every release needs a full announcement. Match the communication to the release type.

| Release Type | Email | Push | Changelog | Social | In-App Pop-up |
|-------------|-------|------|-----------|--------|---------------|
| **Major feature** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Minor feature** | ✅ | Optional | ✅ | Optional | Optional |
| **Bug fix** | ❌ | ❌ | ✅ (brief) | ❌ | ❌ |
| **Hotfix** | ❌ | ❌ | ❌ | ❌ | ❌ |

> **Rule: No communication goes out until the smoke test has passed and PM has confirmed production is stable.**

---

## 16 — Release Communication Flow

Once production is confirmed stable, execute in this order:

```
1. Publish changelog  →  leadpulze.com/updates
         ↓
2. Send product email  →  within 24 hours of stable deploy
         ↓
3. Enable in-app pop-up  →  same day as email
         ↓
4. Send push notification  →  24–48 hours after email
         ↓
5. Post on social media  →  same day as email
```

### Timing Summary

| Channel | Timing |
|---------|--------|
| Changelog | Same day as deploy |
| Email | Within 24 hours of stable deploy |
| In-app pop-up | Same day as email |
| Push notification | 24–48 hours after email |
| Social media | Same day as email |

---

## 17 — Email Announcement

**Owner:** Product Marketing  
**Timing:** Within 24 hours of production being confirmed stable

### Subject Line

```
New in LeadPulze: [Feature Name]
```

### Email Structure

| Section | Content guidance |
|---------|-----------------|
| **Opening** | One sentence: what's new and why it matters |
| **The problem** | What users struggled with before this feature |
| **The solution** | What the feature does and the core benefit |
| **How to use it** | 2–3 steps or a link to the help article |
| **CTA** | Clear button: "Try it now" → deep link to the feature |
| **Footer** | Unsubscribe link + support contact |

---

## 18 — Mobile Push Notification

**Owner:** Product Marketing  
**Timing:** 24–48 hours after the email is sent (not on the same day)

### Title (max 50 characters)

```
🚀 [Feature Name] is now live
```

### Body (max 100 characters)

```
[One line describing the core benefit — e.g. "Track your pipeline in real time."]
```

### Rules

- Do not send on the same day as the email
- Send between 9am–6pm in the user's local timezone
- Link directly to the new feature, not the app homepage

---

## 19 — In-App Pop-up

**Owner:** Engineering / Product Marketing  
**Timing:** Enabled same day as the email

### Behaviour

- Shows **once per user** on their next login after the feature is enabled
- Permanently dismissed after the user closes it
- Do not show mid-task — trigger on the main dashboard only

### Content Structure

| Element | Guidance |
|---------|---------|
| **Headline** | Feature name + one-line benefit |
| **Body** | 1–2 sentences max |
| **Visual** | Feature GIF or screenshot (strongly recommended) |
| **CTA button** | "Try it" → takes user directly to the feature |
| **Dismiss** | Clear close button, always visible |

---

## 20 — Public Changelog

**Owner:** Product Marketing  
**Published at:** leadpulze.com/updates  
**Timing:** Same day as production deploy

### Entry Format

```markdown
## v1.3.0 — [Feature Name]
Released: [Date]

[One sentence summary of the feature and the problem it solves.]

**What's new**
- [Key change or addition]
- [Key change or addition]
- [Key change or addition]

**Who benefits**
[User segment or role this helps most]

[Read the guide →](link)  |  [Watch the demo →](loom-link)
```

---

## 21 — Social Media

**Owner:** Product Marketing  
**Timing:** Same day as email (within 48 hours of deploy)

### Platforms & Format

| Platform | Format | Tone |
|----------|--------|------|
| **LinkedIn** | Text (150–300 words) + image or GIF | Professional, business value focused |
| **Twitter / X** | 1–3 tweets, short + punchy | Conversational, product-led |
| **Instagram** | Visual-first — GIF, screenshot, or short demo clip | Clean, product showcase |
| **Product Hunt** | Full launch post with description and assets | Only for MAJOR version releases |

### Post Structure

1. **Hook** — one line that stops the scroll
2. **Problem** — what pain does this solve?
3. **Feature** — what did we ship?
4. **CTA** — link to try it or read more
5. **Visual** — GIF, screenshot, or short video (always include one)

---

## 22 — Sales Enablement Pack

**Owner:** Sales + Product Marketing  
**Required for:** All major feature releases  
**Ready by:** Before internal briefing

### Pack Contents

| Asset | Description |
|-------|-------------|
| **Demo video** | The Loom recording from the release — 30 sec to 2 min |
| **Feature brief (1-pager)** | Problem → Solution → Key benefits → Who it's for |
| **FAQ doc** | 5–10 common questions with answers |
| **Pitch script** | How to introduce the feature naturally in a sales call |
| **Objection handling** | Likely pushbacks and suggested responses |

### Storage

```
Notion → Sales Enablement → Releases → v[X.X.X] — [Feature Name]
```

---

## 23 — Feature Adoption Monitoring

**Owner:** Product Manager  
**Tools:** PostHog / Datadog

Monitor at three checkpoints after every release:

| Checkpoint | When | What to look for |
|------------|------|-----------------|
| **Day 3** | 3 days post-deploy | Is anyone using it? Any early errors or support spikes? |
| **Day 7** | 7 days post-deploy | Are users returning? Is activation trending up or flat? |
| **Day 14** | 14 days post-deploy | Are we hitting the success metric? Input for review meeting. |

### Metrics (set targets per feature at release time)

| Metric | Definition |
|--------|-----------|
| **Activation rate** | % of eligible users who used the feature at least once |
| **Engagement** | Average sessions or key actions per active user per week |
| **Retention** | % of users who return to the feature in week 2 |
| **Error rate** | Feature-related errors per 1,000 sessions (target: <0.5%) |
| **Support tickets** | Volume of tickets tagged to this feature |

### Feature-Specific Metric Examples

| Feature | Success Metric |
|---------|---------------|
| Voice capture | % of leads captured via voice |
| Auto follow-up | % of active leads receiving automated follow-up |
| Sales reporting | Reports generated per user per week |

---

## 24 — Customer Feedback Collection

**Owner:** Customer Success  
**Timing:** Ongoing from launch day

### Collection Methods

| Method | When to use | Tool |
|--------|------------|------|
| **In-app survey** | 3–5 days after user activation | PostHog or Typeform |
| **NPS survey** | 7–14 days after activation | Delighted or Typeform |
| **Customer interview** | For power users or users who churned | Calendly + Zoom |
| **Support ticket review** | Ongoing | Linear / Jira |
| **Email reply monitoring** | Monitor replies to the launch email | Resend dashboard |

### Key Questions to Ask

- Did this feature solve the problem you had?
- What is missing or could be better?
- How often do you expect to use this?
- Would you recommend this to a colleague?

Customer Success shares a written feedback summary with Product by Day 14.

---

## 25 — Post-Release Review

**Owner:** Product Manager  
**When:** 14 days after launch  
**Format:** 45-minute team meeting

### Attendees

Engineering · Product · QA · Marketing · Customer Success · Sales (optional)

### Agenda

| Topic | Time |
|-------|------|
| Adoption metrics review (Day 3, 7, 14) | 10 min |
| Bugs reported and resolved | 5 min |
| Customer feedback summary | 10 min |
| What went well in this release | 5 min |
| What should we improve next time | 10 min |
| Action items and owners | 5 min |

### Outcome for Each Feature

After reviewing, the team assigns one of three outcomes:

| Outcome | Meaning |
|---------|---------|
| ✅ **Keep** | Feature is working. Continue monitoring. |
| 🔧 **Improve** | Feature has potential but needs iteration. Log tickets. |
| ❌ **Deprecate** | Feature is not being used. Plan removal. |

### Outputs

- Written summary added to the release doc in Notion
- Action items logged in Linear / Jira with owners and due dates
- Any SOP improvements flagged to Product team for next revision

---

## Master Release Flow

Use this as your end-to-end reference on every release day.

| # | Step | Owner | Phase |
|---|------|-------|-------|
| 1 | Feature developed on branch | Engineer | Build |
| 2 | PR opened, reviewed, approved | Engineer + Lead | Build |
| 3 | Version tagged (SemVer) | Engineering Lead | Build |
| 4 | Release document completed in Notion | Product Manager | Prepare |
| 5 | QA testing complete on staging | QA Lead | Prepare |
| 6 | Feature flag created in LaunchDarkly | Engineer | Prepare |
| 7 | Sales enablement pack ready (major features) | Sales + Marketing | Prepare |
| 8 | Internal teams briefed | Product Manager | Prepare |
| 9 | Definition of Done checklist signed off | Product Manager | Prepare |
| 10 | Deploy to staging | DevOps | Deploy |
| 11 | QA sign-off on staging | QA Lead | Deploy |
| 12 | PM go/no-go | Product Manager | Deploy |
| 13 | Enable feature flag (Internal stage) | Engineer | Deploy |
| 14 | Deploy to production | DevOps | Deploy |
| 15 | Smoke test passes | QA Lead | Deploy |
| 16 | PM confirms production stable | Product Manager | Deploy |
| 17 | Publish changelog | Marketing | Announce |
| 18 | Send launch email | Marketing | Announce |
| 19 | Enable in-app pop-up | Marketing / Eng | Announce |
| 20 | Send push notification (24–48h later) | Marketing | Announce |
| 21 | Post on social media | Marketing | Announce |
| 22 | Day 3 metrics review | Product Manager | Learn |
| 23 | Day 7 metrics review | Product Manager | Learn |
| 24 | Day 14 post-release review meeting | Full Team | Learn |

---

*LeadPulze Product Release SOP — v2.0 — Questions or suggested changes? Ping the Product team in #releases.*
