---
layout: default
---

# SOP – If Glitch Image in Green Camera

## Purpose
To outline the steps required for identifying, documenting, and reporting occurrences of glitch images in the **GreenCam** system for effective troubleshooting and root cause analysis.

## Scope
This SOP applies to all personnel involved in the operation, maintenance, and support of the GreenCam system.

## Responsibilities
- **Validation Team / Service Team**: Collect data and document incidents.
- **Software Team**: Analyse the data and provide insights for root cause analysis.
- **Concerned Stakeholders**: Validate findings and recommend corrective actions.

---

## Procedure

### Step 1: Collect Glitch Images

1. **Identify Glitch Occurrence**
   - Observe and identify any images exhibiting glitches in the GreenCam system.

2. **Save Glitch Images**
   - Capture and save all identified glitch images in a designated folder.

3. **Send Images**
   - Email or share the collected glitch images with the software team for further analysis.

---

### Step 2: Record Current Environment Metrics

1. **Environmental Recording**
   - Do **not** reboot the system on any occurrence.
   - Perform earthing voltage testing.
   - Use a monitoring tool to record the current environment settings without making any changes.

2. **Collect Hardware Metrics**
   - Record the following:
     - Voltage
     - Temperature
     - Current readings from relevant sensors

3. **Collect Software Metrics**
   - Record the following:
     - RAM usage
     - Memory consumption
     - Status of live camera
     - Docker container status

4. **Document Metrics**
   - Ensure all metrics are documented clearly and concisely for review.

---

### Step 3: Check Hardware Components

1. **Inspect Components**
   - Physically inspect the following:
     - Camera flex cable
     - LAN cable
     - Raspberry Pi power cable
     - Camera sensor

2. **Record Findings**
   - Document any visible damage or abnormalities in the components.

---

### Step 4: Create Incident Report

1. **Compile Information**
   - Gather all data collected in the previous steps, including:
     - Glitch images
     - Environmental metrics
     - Hardware inspection results

2. **Draft Incident Report**
   - Include:
     - Description of the glitch occurrence
     - Time and date of occurrence
     - Steps taken during investigation
     - Findings from hardware and software metrics

3. **Send to Software Team**
   - Submit the incident report to the software team for validation and further analysis.

---

## Record Keeping

- All incident-related documentation must be stored in a designated folder accessible to authorised personnel.
- Retain records based on occurrence type:
  - **Rare**: Record roll and doff numbers.
  - **Frequent**: Record roll details, start time, stop time, and other useful insights.
- If required, and with approval from the Software Team, the **entire cabinet with all components** must be brought back to the office for testing.

---
