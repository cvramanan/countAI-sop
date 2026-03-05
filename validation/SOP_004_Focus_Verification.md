# KNIT-I SYSTEM — STANDARD OPERATING PROCEDURE  
## SOP-KNITI-01: Focus Verification & Settings

# 1. Objective
To ensure all fixed industrial cameras on the **KNIT-I machine** are correctly focused, configured, and capable of detecting defects with full clarity before system go-live.

**Time Required:** Full verification must be completed within **2 hours of installation**.  
**SLA:** Verification must be completed and approved **before any production run begins**.

---

# 2. Scope
- Applicable for all new **KNIT-I machine installations**.  
- Executed by the **Field Engineer on-site**.  
- Approved by **Validation Engineer**.

---

# 3. Trigger Condition

| Field | Detail |
|------|-------|
| **Trigger** | Every new KNIT-I machine installation |
| **Executed By** | Field Engineer (on-site) |
| **Approved By** | Validation Engineer |
| **Time Limit** | Must be completed within **2 hours of hardware mounting** |

---

# 4. Settings Verification Requirements

The Field Engineer must verify all settings against the **approved project specification sheet**.  
Every setting must match exactly — **partial match is not acceptable**.

| # | Setting Parameter | Expected Value | Status |
|--|------------------|---------------|-------|
| 1 | Camera Resolution / Image Size | As per approved spec sheet | Pass / Fail |
| 2 | Exposure & Lighting Settings | As per approved spec sheet | Pass / Fail |
| 3 | Frame Rate / Capture Interval | As per approved spec sheet | Pass / Fail |
| 4 | Model Inference Threshold Settings | As per approved spec sheet | Pass / Fail |

---

# 5. Physical Inspection Requirements

## 5.1 Camera Lens & Housing Check
- Inspect camera housing — **no visible cracks, dents, or damage**.
- Lens must be clean — **no dust, smudging, or condensation**.
- Apply permanent **reference marking on lens**:
  - Draw a clear line from **aperture ring to focus screw region**  
  *(ref: Accuracy Points SOP)*.
- Manually adjust focus ring until **sharpest image** is visible on reference target or live fabric surface.

---

## 5.2 Camera Mounting Alignment
- Draw position markings on both **camera mounting clamps**:
  - Horizontal position  
- Use a **permanent visible marker**.
- Markings must **not rub off during cleaning**.
- Capture **reference photo of mounting position** and store in installation record.

---

## 5.3 Lighting Fixture Check
- Verify all **lighting fixtures are operational** and correctly positioned.
- Draw position markings on **light mounting clamps** for **Cam 1 and Cam 2**.
- Ensure:
  - No shadows  - 
  - No uneven illumination
- Lighting intensity must match **approved specification**.

---

## 5.4 Network & Connectivity Check
- Camera connected to system controller.
- Confirm **live feed with zero latency**.
- Verify:
  - IP address
  - Port configuration
  - Communication protocol  
- Must match **system requirements**.

⚠ **If physical damage is observed:**
- Photograph immediately.
- Inform **Project Manager**.
- Do **not proceed** without approval.

---

# 6. Defect Visibility & Clarity Verification

Using a **test fabric sample with known defects**, all **5 criteria** must be confirmed as **PASS** before sign-off.

A single **FAIL** means verification has **not passed**.

| # | Defect Visibility Check Criterion | Result | Remarks |
|--|----------------------------------|--------|--------|
| 1 | Defect clearly distinguishable from background fabric | Pass / Fail | |
| 2 | Minimum defect size visible at camera resolution | Pass / Fail | |
| 3 | No blur or overexposure on defect region | Pass / Fail | |
| 4 | Defect visible across all lighting conditions | Pass / Fail | |
| 5 | Field Engineer visually confirms defect | Pass / Fail | |

---

# 7. Step-by-Step Procedure

| Step | Action | Details |
|----|------|------|
| 1 | Open Camera Config  | Access KNIT-I Live camera field, confirm Visibility and Exposure details|
| 2 | Verify Software Settings | Cross-check all Section 4 settings against approved spec sheet |
| 3 | Physical Inspection | Complete all checks in Section 5 |
| 4 | Apply Reference Markings | Mark lens position, camera mount, and light clamps |
| 5 | Manual Focus Adjustment | Rotate focus ring until sharpest image is achieved |
| 6 | Capture Reference Test Image | Confirm sharpness, exposure |
| 7 | Defect Visibility Test | Place test fabric and verify Section 6 criteria |
| 8 | Complete Verification Log | Fill all fields in Focus Verification Log |
| 9 | Submit for Approval | Share checklist with Validation Engineer |

---

# 8. Escalation Protocol

| Issue | Action | Escalation if Unresolved |
|-----|------|------|
| Settings mismatch | Re-configure and re-verify | Escalate to remote team after 2 attempts |
| Physical damage | Photograph and inform PM | Installation halted until approval |
| Defect not visible | Adjust focus and lighting | Escalate to CV/ML team |
| Network failure | Check cables and IP settings | Escalate to IT within 30 minutes |
| Approval pending | Log pending status | Follow up with Validation Engineer |

🚫 **Installation must not proceed until all FAIL items are resolved and written approval is received.**

---

# 9. KPIs & Acceptance Criteria

| Metric | Target |
|------|------|
| Verification completion time | Within 2 hours |
| Settings match rate | 100% |
| Defect visibility pass rate | 100% |
| Reference markings applied | 100% installations |
| Installation without sign-off | 0 |

---

# Acceptance Checklist

- [ ] All settings verified and match spec sheet  
- [ ] All physical checks passed  
- [ ] Reference markings applied  
- [ ] All defect visibility criteria passed  
- [ ] Focus Verification Log completed  
- [ ] Validation Engineer approval received  

---

# 10. Focus Verification Log

| Field | Entry |
|------|------|
| Machine ID / Serial Number | |
| Customer Name | |
| Installation Site / Location | |
| Date of Verification | |
| Field Engineer Name | |
| Software Version | |
| Overall Status (Pass / Fail) | |
| Remarks / Issues Observed | |


