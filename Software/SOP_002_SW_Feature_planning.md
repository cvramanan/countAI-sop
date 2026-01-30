# Feature Planning SOP for Software Teams

**Document Type:** Standard Operating Procedure (SOP)  
**Version:** 1.0  
**Last Updated:** January 2026  
**Applies To:** Product, Engineering, Design, Data, Leadership  
**Owner:** Product Team

---

## 1. Purpose

This document defines a **standard, repeatable, and scalable process** for feature planning in software teams.

The goal is to ensure that every feature:

* Solves a **real user problem**
* Aligns with **business objectives**
* Is **prioritized objectively**
* Is **well-scoped, measurable, and iterative**
* Creates value for users and captures value for the business

---

## 2. Scope

This SOP applies to:

* New feature development
* Feature improvements and iterations
* Experimental and MVP features
* Platform, AI, infra, and UX features

This SOP does **not** cover:

* Bug fixes (handled via bug triage SOP)
* Operational or infra-only tasks unless user-facing impact exists

---

## 3. Core Feature Planning Principles (Global Best Practices)

These principles are mandatory and override all opinions.

### 3.1 Outcome Over Output

* Features are planned to achieve **outcomes**, not to ship functionality.
* Every feature must be tied to at least **one measurable metric**.

**Bad Example:**  
Build AI summary feature

**Good Example:**  
Reduce user time spent reviewing leads by 30%

---

### 3.2 Evidence-Based Decision Making

Feature decisions must be backed by:

* User interviews
* Product analytics
* Support or sales data
* Revenue or retention impact

**No evidence = No prioritization**

---

### 3.3 Small Bets, Fast Feedback

* MVP first, not perfection
* Validate assumptions quickly
* Iterate based on real usage

---

### 3.4 Clear Ownership (DRI Model)

* Every feature has **one DRI (Directly Responsible Individual)**
* The DRI is accountable for:

  * Problem definition
  * Scope clarity
  * Delivery
  * Success measurement

Shared ownership is not allowed.

---

### 3.5 User Value Before Business Value

* If a feature does not clearly benefit users, it should not be built.
* Business value follows user value.

---

## 4. Roles & Responsibilities

### 4.1 Product Manager / Feature Owner

* Owns the problem and outcome
* Writes the feature brief
* Defines success metrics
* Drives prioritization

### 4.2 Engineering

* Provides technical feasibility
* Estimates effort
* Flags risks and dependencies
* Owns implementation quality

### 4.3 Design

* Owns UX and usability
* Validates flows and edge cases
* Ensures simplicity and clarity

### 4.4 Data / Analytics (if applicable)

* Validates metrics
* Sets up dashboards
* Helps interpret post-launch results

---

## 5. Feature Planning Lifecycle

### STEP 1: Feature Intake

#### 5.1 Feature Sources

* User feedback
* Customer support tickets
* Sales and CS insights
* Product analytics
* Leadership or founder input

#### 5.2 Feature Intake Template

```text
Feature Name:
Problem Statement:
Who is affected:
Frequency of the problem:
Current workaround:
Evidence (user quotes, data, tickets):
Expected user impact:
Expected business impact:
```

**Rule:** Features without evidence cannot move forward.

---

### STEP 2: Problem Validation

#### 6.1 Validation Questions

* Is this problem painful enough for users?
* How many users are affected?
* Is it frequent or rare?
* Does it block activation, retention, or revenue?
* Can it be measured?

#### 6.2 Validation Methods

* 5–10 qualitative user interviews
* Funnel or cohort analysis
* Support ticket volume analysis
* Session recordings or heatmaps

---

### STEP 3: Define Success Metrics (Before Building)

Each feature must define success before development begins.

#### 7.1 Metrics Requirements

1. Primary Metric (mandatory)
2. 1–2 Secondary Metrics (optional)

#### 7.2 Example Metrics

| Feature Type           | Primary Metric      |
| ---------------------- | ------------------- |
| Onboarding improvement | Activation rate     |
| AI automation          | Time saved per user |
| Dashboard              | Weekly active users |
| Lead scoring           | Conversion rate     |

---

### STEP 4: Feature Prioritization

#### 8.1 Primary Framework: RICE

**RICE Score = (Reach × Impact × Confidence) / Effort**

**Definitions:**

* **Reach:** Number of users impacted
* **Impact:** Value per user (low / medium / high)
* **Confidence:** Data certainty (0–100%)
* **Effort:** Engineering + design effort

Features are ranked by RICE score.

---

#### 8.2 Fast Alternative (Early-Stage Teams)

**Impact vs Effort Matrix:**

|                 | Low Effort | High Effort    |
| --------------- | ---------- | -------------- |
| **High Impact** | Build now  | Plan carefully |
| **Low Impact**  | Optional   | Drop           |

---

### STEP 5: Feature Brief (Mandatory)

No development work can start without an approved Feature Brief.

#### 9.1 Feature Brief Template

```text
Feature Name:
Owner (DRI):
Problem Statement:
User Persona:
User Journey Impacted:
Proposed Solution:
Out of Scope / Non-Goals:
Success Metrics:
Assumptions:
Dependencies:
Risks:
```

*This document is the single source of truth.*

---

### STEP 6: Solution Design & Review

#### 10.1 Participants

* Product
* Engineering
* Design
* Data (if applicable)

#### 10.2 Design Principles

* Explore multiple solution options
* Choose the simplest viable approach
* Design for edge cases early
* Avoid over-engineering

---

### STEP 7: MVP Scope Definition

#### 11.1 MVP Rules

* MVP must validate the core hypothesis
* MVP must be usable by real users
* MVP must be measurable

#### 11.2 Scope Definition

```text
IN SCOPE:
OUT OF SCOPE:
PHASE 2 / FUTURE:
```

*If MVP exceeds 2 sprints → rescope.*

---

### STEP 8: Engineering Planning

#### 12.1 Required Outputs

* Technical design overview
* Architecture impact
* API / data model changes
* Effort estimation
* Risk assessment

#### 12.2 Estimation Rule

If estimate is unclear → break down further.

---

### STEP 9: Execution & Tracking

#### 13.1 Sprint Execution

* Daily standups (blockers only)
* Sprint demo at end
* Clear acceptance criteria

#### 13.2 Tracking

* Feature status board
* Weekly owner updates
* Clear "at risk" flags

---

### STEP 10: Launch Readiness

#### 14.1 Launch Checklist

* [ ] Feature flag enabled (if applicable)
* [ ] QA completed
* [ ] Analytics tracking verified
* [ ] Documentation updated
* [ ] Rollback plan ready

---

### STEP 11: Post-Launch Review (Mandatory)

#### 15.1 Review Timing

7–14 days after launch

#### 15.2 Review Questions

* Did we hit the success metrics?
* What worked better than expected?
* What failed or surprised us?
* What should we change next?

#### 15.3 Outcomes

* Iterate
* Scale
* Pause
* Kill the feature (learning documented)

---

## 6. Definition of Done (Feature-Level)

A feature is considered **DONE** only when:

* [ ] Released to users
* [ ] Metrics are live and tracked
* [ ] Post-launch review completed
* [ ] Learnings documented

---

## 7. Common Feature Planning Anti-Patterns

* Building without metrics
* Over-scoped MVPs
* Stakeholder-driven features
* Shipping without post-launch analysis
* Confusing activity with impact

---

## 8. Continuous Improvement

This SOP must be reviewed:

* Quarterly
* After major failures
* When team or product stage changes

Improvements should be versioned and documented.

---

## 9. Appendix

### A. Feature Kill Criteria

* No measurable impact
* Low adoption after iteration
* High complexity, low value
* Strategy misalignment

*Killing features is considered a success, not a failure.*
