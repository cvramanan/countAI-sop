---
layout: default
---

# SOP_002_GIT VERSION CONTROL

---

## 1️. Purpose

To ensure:

- Controlled code changes  
- Zero direct production edits  
- Clear branching strategy  
- Clean commit history  
- Easy rollback capability  

---

## 2️. Scope

Applies to:

- All repositories  
- Backend + Frontend  
- Infrastructure code  
- CI/CD configurations  

---

## 3. Branching Strategy (Recommended – Git Flow Lite)
main → Production (Stable)
develop → Staging / Pre-production
feature/* → New features
bugfix/* → Non-critical bug fixes
hotfix/* → Production fixes
release/* → Release preparation branch


---

## 🏗 Branch Purpose Explained

| Branch     | Purpose                     | Merge Into        |
|------------|-----------------------------|-------------------|
| feature/*  | Build new feature           | develop           |
| bugfix/*   | Fix dev bugs                | develop           |
| release/*  | Pre-release stabilization   | main + develop    |
| hotfix/*   | Urgent production fix       | main + develop    |

---

## 4. Workflow Process

### Step 1: Feature Development

```bash
git checkout develop
git pull origin develop
git checkout -b feature/auto-priority-engine
```

Develop → Commit → Push → Create PR to develop

### Step 2: Pull Request Rules

PR must include:

Feature ID

Description

Testing steps

Screenshots (if UI)

Risk impact

⚠ No direct push to main

### Step 3: Release Preparation

When ready to release:

git checkout develop
git checkout -b release/v1.2.0

QA testing

Minor fixes allowed

Version updated

Merge:

release → main

release → develop

Tag release:

git tag v1.2.0
git push origin v1.2.0


### Step 4: Hotfix Workflow

If production issue:

git checkout main
git checkout -b hotfix/login-crash

Fix → PR → Merge into:

main

develop

Tag:

v1.2.1
## 5. Versioning Standard (Semantic Versioning)

Format:

MAJOR.MINOR.PATCH
Version	Meaning
1.0.0	Initial release
1.1.0	New feature
1.1.1	Bug fix
2.0.0	Breaking change

Reference standard maintained by SemVer.

## 6. Commit Message Convention

Format:

type(scope): short description
Types:

feat

fix

refactor

chore

docs

test

Example:
feat(priority): add auto-priority calculation logic
fix(auth): resolve token refresh issue
## 7. Protection Rules

Branch protection (must enable on Git platform):

Require PR approval

Require CI checks

Prevent force push

Restrict who can merge

Common Git platforms:

GitHub

GitLab

Bitbucket

## 8. CI/CD Integration

Before merge:

Lint passes

Tests pass

Build success

No security warnings

Optional tools:

SonarQube

CircleCI

GitHub Actions

## 9. Emergency Protocol

If main branch breaks:

Stop deployments

Revert to last stable tag

Create hotfix branch

Root cause analysis

Document incident

## 10. Git Hygiene Rules

One feature per branch

Small PRs (< 400 lines recommended)

Delete merged branches

Rebase before merge (if clean history needed)

Avoid long-running branches
