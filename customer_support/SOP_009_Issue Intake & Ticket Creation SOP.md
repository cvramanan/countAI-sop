# SOP: Issue Intake & Ticket Creation


# 1. Purpose

The purpose of this SOP is to define a **structured, time-bound, and measurable process** for receiving, validating, and creating support tickets for all reported issues.

This ensures:

- No issue is missed
- Accurate documentation
- SLA compliance
- Faster troubleshooting and resolution

---

# 2. Scope

This SOP applies to:

- Customer-reported issues
- Internal team-reported issues
- Monitoring or system-generated alerts

This SOP covers only **issue intake and ticket creation (Level 1 Support stage)**.

---

# 3. Ticket Creation SLA (Mandatory)

All reported issues must be converted into a ticket within the following timelines:

| Priority | Ticket Creation SLA |
|---------|--------------------|
| P1 (Critical) | Within 15 minutes |
| P2 | Within 30 minutes |
| P3 | Within 1 hour |
| P4 | Within 2 hours |

Failure to create a ticket within the defined SLA will be considered **SLA non-compliance**.

---

# 4. Mandatory Ticket Fields (Non-Negotiable)

A ticket **must not be saved or escalated** unless the following mandatory information is captured.

---

## 4.1 Reporter Information

- Customer / Mill Name (Mandatory)
- Contact Number or Email (Mandatory)

---

## 4.2 Product Details

- Product Name (Mandatory)
- Machine Number / Device ID (Mandatory)
- Location / Department (if applicable)

---

## 4.3 Issue Information

- Clear Issue Description (Minimum two sentences)
- Issue Scenario / Steps where the issue occurred
- Date & Time of Occurrence
- Frequency (One-time / Intermittent / Continuous)
- Error Message or Alarm Code (if available)
- Attachments (Screenshot / Log / Image)

⚠️ **Mandatory for P1 and P2 issues**

Tickets with missing mandatory fields **must not proceed to escalation**.

---

# 5. Ticket Creation Process

---

## Step 1: Acknowledge the Issue

- Acknowledge the issue within SLA (as defined in Customer Response SOP).
- Inform the customer that the issue has been logged and is under review.

---

## Step 2: Validate Information

- Verify the completeness of issue details.
- Request additional information if required.
- For **P1 issues**, do not delay ticket creation while waiting for additional information.

---

## Step 3: Create Ticket

- Log into the ticketing system.
- Enter all mandatory fields accurately.
- Assign priority based on the priority matrix.
- Use a clear and meaningful ticket title.

### Example Ticket Title
ABC Mill – Machine 29 – Camera No Signal

---

# 6. Priority Assignment Matrix

| Impact | Production Down | Partial Impact | Minor Impact |
|------|-----------------|---------------|-------------|
| Urgent | P1 | P2 | P3 |
| Non-Urgent | P2 | P3 | P4 |

Incorrect priority assignment will be treated as a **ticket quality deviation**.

---

# 7. Ticket Quality Standards

A ticket is considered **high quality** only if it includes:

- Clear problem statement
- Actual result vs expected result
- Steps to reproduce (if applicable)
- Proper attachments (images, logs, screenshots)
- Initial assessment by L1 support engineer

---

### Unacceptable Example

> Machine not working.

---

### Acceptable Example

> Machine 29 camera feed not detected after system restart. Error code 504 displayed. Issue started at 10:30 AM.

---

# 8. Initial Ownership Policy

- All newly created tickets remain under **L1 Technical Support ownership** until initial verification is completed.
- Tickets must not be directly assigned to **Software or Hardware teams** without initial review.
- Escalation requires **complete documentation**.

---

# 9. Performance Metrics (KPIs)

The following KPIs will be measured monthly.

---

## 9.1 Ticket Creation SLA Compliance

Percentage of tickets created within SLA.

**Target:** ≥ 98%

---

## 9.2 Ticket Quality Score

Random audit of 10% of tickets for completeness.

**Target:** ≥ 95%

---

## 9.3 Missing Mandatory Field Rate

Percentage of tickets with missing mandatory information.

**Target:** 0%

---

## 9.4 Incorrect Priority Assignment Rate

Percentage of tickets assigned incorrect priority.

**Target:** ≤ 3%

---

# 10. Monitoring & Compliance

---

## Daily Monitoring

- Support Lead reviews newly created tickets for SLA compliance.

---

## Weekly Audit

- Random review of **10% of tickets**
- Check ticket completeness, attachments, and priority accuracy

---

## Monthly Report Must Include

- Total tickets created
- SLA compliance percentage
- Ticket quality audit score
- Escalation rate

---

# 11. Escalation for Non-Compliance

If SLA breach or ticket quality deviation occurs:

- **1st occurrence** → Verbal reminder  
- **2nd occurrence** → Written warning  
- **Repeated non-compliance** → Escalation to Operations Manager

---

# 12. Exception Handling

For **P1 Critical Outage**:

- Create ticket immediately with available information.
- Update remaining details within **1 hour**.
- Inform Support Lead immediately.

---

# 13. Review Cycle

This SOP must be reviewed:

- Quarterly, or
- When new tools are introduced, or
- When SLA targets or support processes change

---

# Outcome of This SOP

This SOP ensures:

- No missing information in tickets
- Faster troubleshooting and escalation
- Clear ownership and accountability
- SLA-compliant support operations
