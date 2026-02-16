# Validation Team Workflow 

## Objective

To ensure the successful validation of machine installations and maintain system performance post-deployment through a structured process of evaluation, troubleshooting, and improvement.

---

## Scope

This SOP applies to all validation activities carried out during:

- Initial machine installation  
- Simulation with existing models  
- Post-installation performance checks  
- Handling of customer complaints and system alerts  

---

# 1. Pre-Installation Phase

## 1.1 Machine Installation

- Confirm focus and coverage for each camera or inspection unit.  
- Collect SOP (Standard Operating Procedure) data for all visible defects.  
- Separate the data required for SGP processing.  

---

# 2. Validation Phase

## 2.1 Simulation with Existing Model

- Simulate the collected data using the existing AI model.  

**Decision Flow:**

- ✅ If the model succeeds → Proceed with **Model Deployment**  
- ❌ If the model fails → Proceed to **Data Annotation**  

---

## 2.2 Data Annotation and QC

- Annotate the failed SOP data as per defect types.  
- Perform a QC check on the annotated data.  

**QC Decision:**

- ❌ If QC fails → Re-annotate and perform QC again  
- ✅ If QC passes → Proceed to the training phase  

---

## 2.3 Training and Simulation

Train the model with segregated data types:

- **L1:** SOP data  
- **L2:** Customer complaint simulation  
- **L3:** Surface annotation  

- Simulate again using combined data (**L1 + L2 + L3**).

**Simulation Decision:**

- ✅ If simulation succeeds → Proceed with **Model Deployment**  
- ❌ If simulation fails → Repeat the annotation and QC process  

---

# 3. Post-Installation Monitoring

## 3.1 Monitoring Process

Use software tools to generate performance reports:

- **FPMR** – Performance Report  
- **VMD** – Validation Monitoring Data  

- Validate score using the defined formula.  

---

# 4. Issue Handling

## 4.1 Defects Not Captured

- Check the focus is good or not
- Check Dust/camera alignment changed
- Cross verify the config whether any defect was turned off.
- Collect FDA (False Detection Analysis) data.  
- Simulate the collected FDA data.  
- Analyze the root cause of missed detections.  
- Troubleshoot the issue and implement corrective action.  

---

## 4.2 False Alarms / Naming Mismatch

- Check Machine Parts / Dust accumulations / other disturbance. 
- Collect MDD (Model Detection Data).  
- Simulate false alarm data.  
- Analyze the cause (naming errors, over-sensitive model, etc.).  
- Troubleshoot and fix the false alarm issues.  

---

## 4.3 Customer Complaints

- Directly link to performance report validation steps.  
- Address specific issues raised using FDA or MDD analysis.  
- Feed this data back to annotation and simulation teams if needed.  

---

# 5. Final Steps

- Ensure all validations are documented.  
- Maintain logs of deployed models and performance metrics.  
- Update AI models and training datasets based on feedback cycles.  

---


