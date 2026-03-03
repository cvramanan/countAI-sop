# SOP: Technical Issue Management & Resolution

| Field | Details |
|--------|----------|
| Document Version | 1.0 |
| Effective Date | March 3, 2026 |
| Last Updated | March 3, 2026 |
| Customer Support Team = Document Owner|

---

## 1. Objective

To define a structured workflow for handling technical issues with clear SLAs, escalation procedures, and measurable performance indicators.

---

## 2. Issue Classification

All issues must be categorized at ticket creation.

### 🔴 Critical Issue

- Machine completely stopped  
- System not capturing defects  
- Production fully affected  

### 🟡 Non-Critical Issue

- Minor defect mismatch  
- UI display issue  
- Performance degradation (production running)  

---

## 3. SLA (Service Level Agreement)

| Severity     | Acknowledgement | Initial Analysis | Resolution Target |
|--------------|----------------|-----------------|------------------|
| Critical     | Within 1 hour  | Within 2 hours  | 24 hours         |
| Non-Critical | Within 2 hours | Within 8 hours  | 72 hours         |

⚠️ If resolution exceeds SLA → **Escalation required**

---

## 4. Detailed Workflow Process

### Step 1: Ticket Logging

Ticket must include:

- Machine Number
- Issue description
- Supporting images/videos
- Severity level
- Date & Time of occurrence

---

### Step 2: Initial Troubleshooting (L1 Support)

Performed by Customer Support:

- Basic troubleshooting
- Remote system check
- Log verification
- Restart / configuration validation

**If Fixed:**  
- Update ticket  
- Inform customer  

**If Not Fixed:**  
- Escalate to concerned team  

---

### Step 3: Escalation Matrix

| Issue Type     | Escalate To        | Timeline            |
|----------------|-------------------|---------------------|
| Software Issue | Software Team / PM | Within SLA          |
| Model Issue    | Validation Team    | Within SLA          |
| Hardware Issue | Hardware Team      | Immediate (Critical)|

### Escalation Triggers

- Issue not resolved within defined SLA  
- Same issue repeated 3 times  
- Production fully stopped  

---

### Step 4: Temporary Solution

If permanent fix requires additional time:

- Provide temporary workaround  
- Clearly inform customer  
- Update expected permanent fix date  

---

### Step 5: Permanent Fix

- Document root cause analysis  
- Implement fix  
- Conduct post-fix validation  
- Obtain customer confirmation  

---

### Step 6: Closure Criteria

Ticket can be closed only if:

- Root cause documented  
- Temporary/permanent fix updated  
- Customer informed  
- Validation completed  
- Completion date recorded  

---

## 5. Performance Metrics (KPIs)

To measure support effectiveness:

1. **First Response Time**  
   - Target: 95% within SLA  

2. **Resolution Time Compliance**  
   - Target: 90% within SLA  

3. **Repeat Issue Rate**  
   - Target: < 5%  

4. **Critical Issue Resolution (24 hrs)**  
   - Target: 95%  

5. **Daily Update Compliance**  
   - Target: 100%  

📊 Monthly performance review must be conducted by the Operations Manager.

---

## 6. Escalation Levels

- **Level 1** – Customer Support  
- **Level 2** – Team Lead / PM  
- **Level 3** – Operations Manager  
- **Level 4** – CTO  

🚨 If a critical issue exceeds 24 hours → Mandatory Level 3 escalation.

Flow Chart https://drive.google.com/file/d/1TATcrettCChSqN5O2c9V40pTa2SNDTNT/view?usp=drive_link

---

**Document Type:** SOP  
**Version:** 2.0  
**Owner:** Customer Support Department  
