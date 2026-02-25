---
layout: default
---

# STANDARD OPERATING PROCEDURE (SOP)

## Title: Software Testing and Release Procedure  
**Version:** 1.0.1  
**Effective Date:** 16.02.2026  
**Prepared by:** Siva / Software  
**Approved by:** --  

---

## 1. Purpose

This SOP defines the standardized process for testing, validating, and deploying software updates across mill-side production machines to ensure system stability, controlled rollout, minimal downtime, and proper documentation.

---

## 2. Scope

This procedure applies to:

- Internal office test machines  
- Mill-side production machines  
- Customer production environments managed by the software team  

---

## 3. Objectives

- Ensure software is properly tested before production release.
- Deploy updates in a phased and controlled manner.
- Minimize operational risk and downtime.
- Maintain traceability and rollback capability.
- Document all release activities for auditing and improvement.

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| Developer | Prepare release build and release notes |
| QA / Testing Engineer | Perform functional and regression testing |
| System Administrator | Execute deployment and verify system status |
| Monitoring Engineer | Monitor performance and logs |
| Team Lead / Manager | Approve release stages and final deployment |

---

## 5. Pre-Release Testing Process

Before deployment to any mill-side production machine:

- Code must be merged to the main/release branch.
- Unit and integration tests must be completed.
- QA must validate:
  - Functional requirements  
  - Regression testing  
  - Log validation  
  - Performance checks (if applicable)  
- CI pipeline must pass successfully.
- Release notes must be prepared.
- Backup and rollback plan must be verified.

Only after successful validation can the rollout process begin.

---

## 6. Rollout Strategy

### Stage 0: Internal Office Machine Testing (Mandatory)

- Deploy update to internal office test machines.
- Test duration: **2 to 3 days**.
- Validate:
  - Functionality
  - Logs and error handling
  - Database consistency
  - Network connectivity
  - Performance behavior
- QA approval required before proceeding.

If any issue is detected, fix the issue and restart the process from Stage 0.

---

### Phase 1: Pilot Update (1 Machine)

> **Machine Type:** Mill-side production machine

- Deploy update to **1 mill-side production machine**.
- Monitoring duration: **2 days**.
- Validate:
  - Service stability
  - Logs
  - Resource utilization
  - Error reports
  - 100% of the test cases must pass. If even 1–2% fail, the release will not proceed.
- Proceed only if system is fully stable.

If failed, fix the issue and restart the process from Stage 0.

---

### Phase 2: Controlled Batch (5 Machines)

> **Machine Type:** Mill-side production machines

- Deploy update to **5 mill-side production machines**.
- Monitoring duration: **3 days**.
- Validate:
  - Logs
  - Network connectivity
  - Performance metrics
  - Database health
- Approval required before moving to full rollout.

If failed, fix the issue and restart from Stage 0.

---

### Phase 3: Full Rollout (Remaining Machines)

> **Machine Type:** Remaining mill-side production machines

- Deploy updates in batches of **10 machines per day**.
- Only **10 mill-side production machines per day** must be updated.
- Continue day-by-day until all machines are updated.
- After each daily batch:
  - Verify service health
  - Confirm logs are consistent
  - Check monitoring status
- Final confirmation report must be prepared.

If any batch fails, stop rollout immediately, fix the issue, and restart from Stage 0.

---

## 7. Rollback Procedure

If any issue is detected:

1. Immediately isolate the affected machine.
2. Restore previous stable version from backup.
3. Restart services and verify stability.
4. Log the issue in the incident tracker.
5. Perform root cause analysis.
6. Fix issue before reattempting deployment.

Rollback must be completed within defined recovery time objective (RTO).

---

## 8. Validation and Sign-Off

- QA validation report required for each rollout stage.
- Deployment checklist must be completed and signed.
- Final approval required from Team Lead / Manager.
- Release confirmation email/report to stakeholders.

---

## 9. Documentation and Reporting

Maintain records for:

- Release version details
- Deployment dates and times
- Machines updated
- Incidents and rollbacks
- Monitoring results
- Approval records

All documentation must be stored in the designated project repository.

---

## 10. Tools and Automation

- CI/CD: GitHub Actions  
- Container: Docker  
- Version Control: Git  

(Only the above tools are currently used and followed by the team.)

---

## 11. Sample Release Timeline

- Internal Testing: 2–3 Days  
- Phase 1 (1 Machine): 2 Days  
- Phase 2 (5 Machines): 3 Days  
- Phase 3 (10 Machines Per Day): Day-by-day until completion  

Timeline may vary based on system complexity and risk level.

---

## 12. Post-Deployment Review

- Evaluate uptime and performance.
- Review logs and alerts.
- Document lessons learned.
- Identify improvements for future releases.
- Close release cycle after final approval.

---

**Document Version:** 1.0.1  
**Date:** 16.02.2026  
**Next Review Date:** --  
**Owner:** Software  
