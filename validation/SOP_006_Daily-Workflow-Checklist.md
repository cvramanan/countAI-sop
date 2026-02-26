# STANDARD OPERATING PROCEDURE (SOP)
## VALIDATION TEAM – DAILY WORKFLOW (200MC ORDER)

**Department:** Validation  
**Applicable For:** 200MC Priority Mills  
**Frequency:** Daily  
**Prepared For:** Validation Team  

---

# 1. PRIORITY MILLS CHECK (09:00 AM – 10:30 AM)

## 1.1 Online Status Verification
- Check whether all priority mill machines are online.
- Verify if any error codes are active.
- Record offline machines (if any).

## 1.2 Bypass Checklist & Performance Review
- Review the previous day performance report.
- Identify machines under bypass mode.
- Analyze the reason for bypass.
- Observe performance trend.
- Record findings.

## 1.3 High-Risk Machine Identification
- Filter machines with alarm rate **> 100**.
- Mark them as **High-Risk**.
- Prioritize for detailed analysis.

## 1.4 Spider Chart Analysis
- Open spider graph for each high-risk machine.
- Check:
  - Repeated alarms on same angle of revolution.
  - Machine offline patterns.
  - Zero alarm observations.
- Document abnormal patterns.

## 1.5 Camera & Light Performance Check

### Verify Machine Lights
- ON / OFF status
- Flickering / disturbance

### Inspect Camera
- Focus clarity
- Mounting alignment
- Angle deviation

- Record any misalignment causing false alarms.

## 1.6 Issue Logging
- Log identified issues in the performance report.
- Mention:
  - Machine ID
  - Nature of issue
  - Observation details
- If no issue:
  - Mark as **Verified – No Issue**

---

# 2. ISSUE IDENTIFICATION (10:30 AM – 11:00 AM)

## 2.1 Root Cause Analysis
- Analyze collected data.
- Identify root cause.
- Classify issue into one of the following categories:

### A. Model Issue
- Model not detecting defect / False detection
- Improper training
- Incorrect model mapping

### B. Customer Issue
- Fabric variation
- Tension variation
- Environmental factors

### C. Software Issue
- Configuration errors
- Logic failure
- Sync issues

### D. Hardware Issue
- Camera defect
- Light failure
- Connectivity issue

## 2.2 Ticket Raising (If Required)
- Raise ticket in ticket desk system.
- Mention:
  - Machine ID
  - Issue category
  - Root cause
  - Required action
- Attach supporting data/screenshots.

## 2.3 Fix Plan (For Model Issues)
- Define correction plan:
  - Data collection
  - Model retraining
  - Parameter adjustment
- Assign responsibility.
- Set timeline.

---

# 3. TROUBLESHOOT / CONFIGURATION (11:00 AM – 01:00 PM)

## 3.1 Configuration Verification
Step-by-step check:
- Program information
- Defect control settings
- Camera synchronization
- Stop-line logic
- Alarm thresholds

## 3.2 Configuration Change Logging
- Record every change in configuration ledger.
- Include:
  - Date
  - Machine ID
  - Parameter changed
  - Old value
  - New value
  - Responsible person

## 3.3 False Alarm Analysis
- Analyze why false alarm occurred.
- Check:
  - Light disturbance
  - Camera misalignment
  - Fabric noise
  - Model sensitivity

## 3.4 False Negative Analysis
- Check missed defect cases.
- Verify:
  - Defect type
  - Model confidence
  - Capture timing
- Document reason (Failure Analysis Sheet / Ledger).

## 3.5 Data Collection
Collect:
- Defect images
- Logs
- Alarm data

Store properly for easy retrieval (Store on OneDrive).

## 3.6 Simulation (L1 / L2 / L3)
- Run simulation tests.
- Validate defect detection.
- Compare output with expected results.

## 3.7 Training Requirement
- Identify if retraining is required.
- Mark **Yes / No**.
- If Yes:
  - Schedule data preparation.
  - Initiate model build.

## 3.8 Result Validation
- Confirm issue resolution.
- Cross-check alarm rate.
- Confirm stable performance.

---

# 4. IMPROVEMENT / R&D (02:00 PM – 05:00 PM)

## 4.1 Improvement Task Identification
- Identify recurring issues.
- List improvement opportunities.
- Prioritize based on impact.

## 4.2 Fabric-wise Model Mapping
- Verify model assigned for each fabric type.
- Confirm correct mapping.
- Update if required.

## 4.3 Model Testing / Building
- Test improved model.
- Validate accuracy.
- Deploy if approved.

## 4.4 Documentation
Document:
- Improvement task (Note in Worklog)
- Changes made (Note in Ledger)
- Results achieved (Note in Worklog)

---

# DAILY COMPLETION CHECKLIST

- [ ] Priority mills reviewed  
- [ ] Issues logged  
- [ ] Root cause identified  
- [ ] Tickets raised (if needed)  
- [ ] Configuration verified  
- [ ] Simulation completed  
- [ ] Improvements documented  
