# LeadPulze Feature Execution SOP

---

# Requirement

Before starting any work, the developer receives these things from the PM and Tech Lead.

**From the PM:**
1. **Feature document** — what the feature does, who uses it, what is out of scope
2. **UI design** — Figma link or screenshots with all screen states

**Requirement meeting is held** — PM explains the feature, developer asks questions, Tech Lead confirms scope. Nothing is built until this meeting is done and everything is clear.

**After the meeting, from the Tech Lead:**

3. **API and data fields** — all endpoints, request fields, and response structure based on the feature
4. **Acceptance criteria** — the list of things that must pass, written by PM and Tech Lead together

---

---

# Development

---

### Git Branching Rules

Before writing any code, make sure you are on the correct branch.

```
main        → production code only. never commit directly here.
develop     → staging. all features merge here first.
feature/*   → your feature work. branch off from develop.
fix/*       → non-urgent bug fixes. branch off from develop.
hotfix/*    → emergency production fixes only. branch off from main.
```

Always create your feature branch from `develop`, not from `main`.

```
Example branch names:
feature/voice-note-capture
fix/note-save-error
hotfix/auth-token-expiry

Workflow:
develop → create feature/voice-note-capture → build → PR → merge back into develop
```

- [ ] Feature branch created from `develop`
- [ ] Branch named correctly with the right prefix
- [ ] Never committing directly to `main` or `develop`

---

### GitHub — How Everything is Managed

All work, documents, bugs, and releases are tracked in GitHub. This is the single source of truth for the engineering team.

**Feature tasks and bugs**

Every feature and every bug must have a GitHub Issue before work starts.

```
For a feature:
Title:    [FEATURE] Voice Note Capture
Label:    feature
Assign:   developer name
Milestone: v1.3.0
Link:     Notion feature document URL

For a bug:
Title:    [BUG] Note not saving on mobile Safari
Label:    bug
Assign:   developer name
Priority: P1 / P2 / P3
Steps to reproduce: written in the issue body
```

Bug priority levels:
```
P1 — production is broken for users. fix immediately.
P2 — major feature broken but app still works. fix in current cycle.
P3 — minor issue, low impact. fix in next release.
```

**Pull Requests**

Every PR must be linked to its GitHub Issue.

```
PR title format:
[FEATURE] Voice Note Capture   → for features
[FIX] Note save on mobile      → for bug fixes
[HOTFIX] Auth token expiry     → for emergency fixes

PR body must include:
- What was built or fixed
- Link to the GitHub Issue  (e.g. Closes #42)
- Screenshots or screen recording
- Acceptance criteria checklist — every item marked pass or fail
```

Writing `Closes #42` in the PR body automatically closes the issue when the PR is merged.

**Labels to use**

```
feature      → new feature work
bug          → something broken
hotfix       → emergency production fix
in progress  → actively being worked on
in review    → PR raised, waiting for review
blocked      → waiting on something before it can move
ready for release → tested and approved, waiting for deploy
released     → shipped to production
```

**Milestones**

Each release version is a Milestone in GitHub.
All issues and PRs for that release are linked to the milestone.

```
Example:
Milestone: v1.3.0
Issues linked:
  #41 — [FEATURE] Voice Note Capture
  #42 — [FIX] Lead search wrong results
  #43 — [FIX] Timeline not refreshing
```

This gives a clear picture of everything going into each release.

**Release notes in GitHub**

When a version is tagged, create a GitHub Release with the changelog:

```
Tag:   v1.3.0
Title: v1.3.0 — Voice Note Capture

Body:  paste the changelog entry here
       (same content as the Notion release document)
```

**Documents**

All technical documents are stored in the repository under a `/docs` folder.

```
/docs
  /features
    voice-note-capture.md       ← technical plan for this feature
  /api
    lead-notes-api.md           ← API endpoint documentation
  README.md                     ← project setup and overview
  CHANGELOG.md                  ← running list of all releases
```

Every time a feature ships, the developer updates the relevant doc files and includes them in the same PR.

Non-technical documents — release documents, incident reports, and internal write-ups — are stored in **Google Docs**, organised in a shared Google Drive folder.

```
Google Drive folder structure:
LeadPulze/
  Releases/
    v1.3.0 — Voice Note Capture.gdoc
    v1.3.1 — Bug Fix Release.gdoc
  Incidents/
    2026-03-12 — Note Save Failure.gdoc
```

- [ ] GitHub Issue created before starting work
- [ ] PR linked to the issue with `Closes #issue-number`
- [ ] Correct label applied to the issue and PR
- [ ] Issue linked to the correct milestone
- [ ] Relevant docs in `/docs` updated in the same PR
- [ ] Release document written in Google Docs
- [ ] GitHub Release created after deploy with the changelog

---

### Step 1 — Read everything before coding

- [ ] Feature document understood
- [ ] UI design and all screen states understood
- [ ] API and all fields understood
- [ ] Acceptance criteria understood

If anything is unclear, ask the PM or Tech Lead before writing any code.

---

### Step 2 — Write your technical plan

Write a short plan and get Tech Lead approval before coding.

```
1. How you will build it
   Example: Use MediaRecorder API to capture audio, send to backend,
   backend calls transcription service, return text to frontend,
   user confirms, then save.

2. New files to create
   Example:
   - src/components/NoteModal.jsx
   - src/services/noteService.js

3. Existing files to change
   Example:
   - src/pages/LeadProfile.jsx — add the Add Note button
   - src/components/LeadTimeline.jsx — show notes in the timeline

4. Database changes
   Example:
   - New table: lead_notes
     (id, lead_id, note_text, note_type, created_by, created_at)

5. Risks or open questions
   Example:
   - MediaRecorder not supported on old iOS — confirm fallback with PM
```

Do not start coding until the Tech Lead approves this plan.

---

### Step 3 — Build the feature

- [ ] Build exactly what is in the feature document, nothing more
- [ ] Handle all screen states: loading, success, error, empty
- [ ] Handle all API errors and show the user a message
- [ ] No hardcoded values — use variables or config
- [ ] No unused code left in

#### Scope Rule

The developer must only build what is defined in the feature document.

If a new idea or improvement appears during development:

1. Stop and document it
2. Do not add it to the current feature
3. Create a new task or backlog item
4. PM decides if it becomes a new feature later

No scope expansion is allowed inside a running feature.

---

### Step 4 — Add analytics events

- [ ] Add PostHog tracking events for all key user actions
- [ ] Verify events are firing before raising a PR

```
Example events:
- note_modal_opened
- note_saved
- note_save_failed
```

---

### Step 5 — Logging

Add logs for every important action in your code. Logs help the team debug issues through monitoring tools like Datadog.

Every log must follow this structure:

```
[EVENT_NAME] user_id=<id> lead_id=<id> action=<what happened> error=<error message or null>

Examples:
[NOTE_SAVE_SUCCESS] user_id=123 lead_id=456 action=save_note error=null
[NOTE_SAVE_FAILED]  user_id=123 lead_id=456 action=save_note error="API timeout"
[NOTE_MODAL_OPENED] user_id=123 lead_id=456 action=open_modal error=null
```

Rules for logging:
- [ ] Log every successful key action
- [ ] Log every error with the error message
- [ ] Never log sensitive data — no passwords, tokens, or personal user data
- [ ] Logs must be readable and consistent in format

---

### Step 6 — Create the PR

- [ ] Title — what feature this is
- [ ] Description — what you built and how
- [ ] Screenshots or screen recording showing it working
- [ ] Acceptance criteria list with every item marked pass or fail
- [ ] Link to the task in the project management tool
- [ ] Any change from the original technical plan noted

---

### Step 7 — Code review and merge

- Tech Lead reviews code quality, security, and performance
- Fix any feedback and update the PR
- Do not merge without Tech Lead approval
- After approval, merge into the `develop` branch

---

---

# Testing

The developer who builds the feature does all testing. There is no separate QA person. The PM reviews and approves the results before release.

---

### Step 1 — Unit testing

Test each function and component on its own.

```
Example:
- saveNote() returns correct response when all fields are valid
- saveNote() throws error when note_text is empty
- Save button is disabled when input is empty
```

- [ ] All unit tests written and passing

---

### Step 2 — Integration testing

Test that frontend and backend work together correctly.

```
Example:
- POST /api/v1/lead-notes saves the note and returns correct response
- GET /api/v1/lead-notes returns the correct list for the lead
- API error is handled and shows the correct message to the user
- Feature flag on — feature is visible
- Feature flag off — feature is hidden
```

- [ ] API calls work end to end
- [ ] Error responses handled correctly
- [ ] Feature flag on and off both work

---

### Step 3 — Acceptance criteria testing

Go through every item from the PM and Tech Lead list. Mark pass or fail.
Every item must pass before raising a PR.

```
Example:
✓ User can open Add Note modal — PASS
✓ User can type and save a note — PASS
✓ Note appears in timeline — PASS
✓ Empty note is blocked — PASS
✗ API error message not showing — FAIL → fix and retest
```

---

### Step 4 — Edge case testing

```
- Empty input — is saving blocked?
- Whitespace only — is saving blocked?
- Very long note — is the limit enforced?
- API failure — is an error message shown?
- Slow internet — is the loading state visible?
- Double clicking Save — does it save twice?
- No permission user — is the button hidden?
- Mobile layout — does it look correct?
- Desktop layout — does it look correct?
```

- [ ] All edge cases tested and handled

---

### Step 5 — Performance checks

The feature must not slow down the app. Check all of the following before raising a PR.

- [ ] Page load time is under ~2 seconds
- [ ] API response time is reasonable — under 500ms where possible
- [ ] No unnecessary API calls happening (no extra calls firing on every render or keystroke)
- [ ] No heavy unnecessary component re-renders

```
How to check:
- Open Chrome DevTools → Network tab → check API call timing
- Open Chrome DevTools → Performance tab → record and check for unnecessary renders
- Check that API calls only fire when they should (e.g. only on Save, not on every keystroke)
```

---

### Step 6 — Security checks

Every feature must pass these security checks before the PR is raised.

- [ ] No sensitive data is logged — no passwords, tokens, user personal data
- [ ] Input is validated on both frontend and backend
- [ ] All API endpoints require authentication — no endpoint is publicly accessible without a token
- [ ] Permissions and roles are verified — a user without the right role cannot access or trigger the feature
- [ ] XSS and injection risks considered — user input is never rendered as raw HTML or passed directly into a query

#### Data Safety Rule

LeadPulze stores customer and sales lead data. Every developer is responsible for protecting it.

- No customer data should appear in logs
- No PII (name, email, phone, company) should appear in error messages shown to the user or written to logs
- API responses must only return the fields the UI actually needs — nothing extra
- Do not send internal database fields (e.g. internal IDs, flags, system metadata) to the frontend

---

### Step 7 — Regression testing

- [ ] Existing features on the same page still work
- [ ] No new console errors or warnings in browser
- [ ] No new console errors in other parts of the app

---

### Step 8 — PM sign-off

- Developer shares the full test results with the PM
- PM reviews the acceptance criteria checklist
- PM confirms the feature is ready for release
- If anything is wrong, developer fixes and retests before release

---

---

# QA — Testing Like a User

QA is not a separate technical person. The PM or anyone on the team does this.
No code knowledge needed. Test the feature exactly like a real user would use it.

---

### What QA tests

**UI**
- Does every screen look correct on desktop and mobile?
- Does the layout match the design?
- Are all buttons, inputs, and labels correct?
- Do loading, success, error, and empty states show correctly?

**Feature functionality**
- Does the feature work the way it was described in the feature document?
- Can you complete the full user flow without any issues?
- Does each step do what it is supposed to do?

**Edge cases — use it the wrong way on purpose**
```
- Click Save without typing anything
- Type only spaces and click Save
- Click Save twice very fast
- Make the internet slow or turn it off and try to save
- Try to use the feature as a user who does not have permission
- Use it on mobile — does everything still work?
- Use it on a small screen — does anything look broken?
```

---

### How to report a bug

If something looks wrong or does not work, write this and send it to the developer:

```
What is broken:
Steps to reproduce:
  1.
  2.
  3.
Expected: what should happen
Actual: what is happening
Screenshot or screen recording attached
```

---

### QA sign-off

When everything looks and works correctly:
- [ ] All acceptance criteria items pass from a user perspective
- [ ] No broken UI on desktop and mobile
- [ ] Edge cases handled correctly
- [ ] No bugs remaining

QA confirms to the PM that the feature is ready. PM gives the final go for release.

---

---

# ✅ Definition of Done

A feature is only complete and ready to release when every single item below is checked.
If any item is not done, the feature does not ship.

- [ ] Feature implemented according to the feature document
- [ ] Technical plan approved by Tech Lead
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] All acceptance criteria fully passing
- [ ] All edge cases handled
- [ ] Analytics events added and verified in PostHog
- [ ] Logging added for all key actions
- [ ] Performance checks passed
- [ ] Security checks passed
- [ ] PR approved by Tech Lead
- [ ] QA sign-off completed
- [ ] Any relevant developer documentation updated (API docs, README, internal docs)
- [ ] Release document written and stored in Notion
- [ ] Feature successfully deployed to staging and confirmed working

---

---

# 🚀 Release

---

### Version number

```
New feature added → change MINOR    e.g. v1.2.0 → v1.3.0
Bug fix only      → change PATCH    e.g. v1.3.0 → v1.3.1
Breaking change   → change MAJOR    e.g. v1.3.0 → v2.0.0
```

Tag in Git:
```bash
git tag v1.3.0
git push origin v1.3.0
```

---

### Release document

PM fills this in Google Docs before every deploy. Deploy does not happen without it.

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LEADPULZE — RELEASE DOCUMENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Feature Name:
Version:
Release Date:
Product Manager:
Engineer:

──────────────────────────────
WHAT IS IN THIS RELEASE
──────────────────────────────
New features:
  List every new feature. If none — write: None

Improvements:
  List anything made better. If none — write: None

Bug fixes:
  Write what was broken and what it does now.
  If none — write: None

Known issues:
  List anything still broken. Include which version it will be fixed in.
  If none — write: None

──────────────────────────────
WHO IS AFFECTED
──────────────────────────────
Which users does this release affect:

What problem does it solve for them:

──────────────────────────────
HOW TO USE THE NEW FEATURE
──────────────────────────────
Steps:
  1.
  2.
  3.

Help article link:

──────────────────────────────
TECHNICAL
──────────────────────────────
Feature flag name:
  Example: feature_voice_note_capture

Rollout stage:
  [ ] Internal   [ ] Beta   [ ] 25%   [ ] 100%

Database changes:
  List new tables, columns, or migrations. If none — write: None

Third-party services added or changed:
  If none — write: None

Rollback plan:
  1. Disable feature flag in LaunchDarkly immediately
  2. Post in #releases — what broke and when
  3. Engineering Lead checks Datadog for error scope
  4. If flag disable is not enough, revert the code and redeploy
  5. Do not re-enable until bug is fixed and retested

──────────────────────────────
SIGN-OFF
──────────────────────────────
Developer name:
Date tested:
All acceptance criteria passed:  [ ] Yes
No blocking bugs remaining:      [ ] Yes
PM reviewed and approved:        [ ] Yes

──────────────────────────────
SUCCESS METRIC
──────────────────────────────
What does success look like:
  Example: 40% of users save at least one note within 7 days.

How we will measure it:
  Example: PostHog event — note_saved — tracked per user per week.

PostHog dashboard link:
Datadog monitor link:

Check-in dates:
  Day 3:   [ ] Reviewed
  Day 7:   [ ] Reviewed
  Day 14:  [ ] Reviewed
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

### Release steps

```
1.  PM release document completed in Notion
2.  Definition of Done checklist fully checked
3.  Developer test results shared with PM
4.  PM signs off
5.  Version number tagged in Git
6.  Feature flag set to Internal in LaunchDarkly
7.  Deploy to staging
8.  Developer tests on staging — confirms it works
9.  PM gives go / no-go
10. Deploy to production
11. Run smoke test immediately after deploy
12. PM confirms production is stable
13. Post-release monitoring begins — 30 minutes
14. Expand feature flag — 25% → 100%
15. Publish changelog
```

---

### Smoke test — run right after every deploy

```
- Can a user log in?
- Can a new lead be created?
- Does the new feature work with the flag enabled?
- Any errors in Datadog?
```

If any of these fail — disable the feature flag immediately. Do not publish the changelog.

---

### Post-Release Monitoring

After every production deploy, the team monitors the system for **30 minutes minimum** before expanding the feature flag rollout.

Check all of the following:

- [ ] Error rate in Datadog — no new spike of errors
- [ ] Analytics in PostHog — events firing correctly, no anomalies
- [ ] Monitoring alerts — no alerts triggered
- [ ] User reports — no incoming reports of broken features in support or Slack

```
If anything looks wrong during the 30 minutes:
→ Disable the feature flag immediately
→ Follow the rollback steps below
→ Do not expand the rollout until the issue is identified and resolved
```

---

### Rollback

```
1. Disable the feature flag in LaunchDarkly
2. Post in #releases on Slack — what broke and when
3. Engineering Lead checks Datadog — how many users affected
4. If flag disable is not enough:
   git revert <merge-commit-hash>
   git push origin main
5. Re-run smoke test to confirm stable
6. Write incident summary and add to the release doc in Google Docs
7. Do not re-enable the flag until bug is fixed and retested on staging
```

---

### Production Incident Rule

If a production issue is affecting users, follow these steps in order. Do not skip any.

```
1. Stop all new deployments immediately
2. Disable the feature flag in LaunchDarkly
3. Notify the team in #incidents on Slack — what is broken and when it started
4. Engineering Lead identifies the root cause using Datadog logs and error traces
5. Fix the issue and retest fully in staging
6. Deploy again only after staging verification passes and PM approves
```

After the issue is resolved, write a short incident report and add it to the release doc in Notion:

```
Incident Report

What happened:
  Describe what broke and what the user impact was.

Root cause:
  What caused the issue.

Fix applied:
  What was changed to fix it.

How we prevent this in the future:
  What process, test, or check will stop this from happening again.
```

---

### Bug Fix Release

If a release contains only bug fixes and no new features, follow the same release steps but fill the release document like this:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LEADPULZE — BUG FIX RELEASE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Version:        e.g. v1.3.1
Release Date:
Engineer:
Product Manager:

──────────────────────────────
BUGS FIXED
──────────────────────────────
For each bug, write:

Bug 1:
  What was broken:
  What it does now:
  How it was found: (user report / internal testing / monitoring alert)

Bug 2:
  What was broken:
  What it does now:
  How it was found:

(add more as needed)

──────────────────────────────
WHAT IS NOT CHANGED
──────────────────────────────
List any areas of the app that were touched but not changed in behaviour,
so QA knows where to do regression testing.

──────────────────────────────
TECHNICAL
──────────────────────────────
Feature flag needed:  [ ] Yes   [ ] No
Rollback plan:
Database changes:     [ ] Yes — describe below   [ ] No

──────────────────────────────
SIGN-OFF
──────────────────────────────
Developer name:
Date tested:
All bug fixes verified:    [ ] Yes
Regression testing done:   [ ] Yes
PM reviewed and approved:  [ ] Yes
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Version for a bug fix release — change the PATCH number only:
```
v1.3.0 → v1.3.1
```

---

### Changelog entry

```
## v1.3.0 — Voice Note Capture
Released: 2026-03-12

Users can now record a voice note on any lead profile.
The note is transcribed and saved to the lead timeline automatically.

New:
- Voice note recording on lead profile
- Auto-transcription of recorded notes

Improvements:
- Lead profile page loads faster

Bug fixes:
- Fixed lead search showing wrong results when filtering by company

Known issues:
- Voice recording not supported on Safari iOS 14 and below. Fix in v1.3.1
```

---

---

# Rules

```
1.  Developer does not start without receiving all 4 requirement items from PM and Tech Lead
2.  Developer does not start without the requirement meeting being done
3.  Developer does not raise a PR without Tech Lead approving the technical plan
4.  Developer does not raise a PR without all testing steps completed
5.  Developer does not raise a PR without every acceptance criteria item passing
6.  Developer does not raise a PR without performance and security checks done
7.  PM reviews and approves test results before QA
8.  QA tests UI, feature functionality, and edge cases like a real user
9.  Definition of Done checklist must be fully checked before release
10. Nothing goes to production without PM sign-off
11. Every release must have a completed release document before deploy
12. Post-release monitoring must run for 30 minutes after every deploy
13. No changelog published until smoke test passes and monitoring is clear
14. Every release must have a feature flag — no direct 100% rollouts
```
