# ServiceNow_ITOM_Project8
AI-Driven CMDB Health &amp; Service Impact Automation (ITOM Simulation)
# 🚀 AI-Driven CMDB Health & Service Impact Automation (ITOM Simulation)

## 🧠 Overview
This project simulates an **AIOps-style CMDB Health Monitoring workflow** using ServiceNow Flow Designer, fully supported on a PDI (no ITOM Licensing required).

When any Configuration Item (CI) becomes **Unhealthy**, the system:

- Automatically generates an **AI-style impact summary**
- Creates a new Incident linked to the CI
- Populates impact/urgency/priority
- Assigns it to the appropriate support group
- Adds detailed reasoning text to help technicians act faster

This mimics real-world ITOM/AIOps root-cause & service-impact analysis.

---

## 🧩 Features

### ✔ AI-Simulated Impact Analysis  
When a CI becomes *Unhealthy*, the system creates intelligent, human-readable summaries.

### ✔ Automated Incident Creation  
The generated Incident includes:
- CI information  
- Impact summary  
- Assignment group  
- Priority escalation  

### ✔ Zero Coding  
Built entirely using:
- Flow Designer  
- CMDB (cmdb_ci)  
- Custom fields  
Fully compatible with PDI environments.

---

## 🏗 Architecture

```
CMDB CI (ai_health_status update)
        ↓
Flow Trigger (Record Updated)
        ↓
AI Impact Summary Creation [Description field]
        ↓
Incident Creation (Auto-assigned, Auto-prioritized)
        ↓
Technician Receives Impact Context
```

---

## 🔧 Technical Steps

### 1️⃣ Create Custom Field  
Table: **cmdb_ci**  
Field: **ai_health_status (Choice)**  
Values: Healthy, Warning, Unhealthy

### 2️⃣ Flow Designer  
Trigger:  
- Record Updated → Table = cmdb_ci  
- Condition: ai_health_status changes to "Unhealthy"

### 3️⃣ Create Incident within Flow  
Fields:
- Short description → `[AI] CI Unhealthy – ${Trigger.record.name}`
- Description → AI-style summary using data pills
- Configuration item → Trigger → Record
- Impact/Urgency/Priority = High
- Assignment group = Service Desk / Network Support

### 4️⃣ Test  
Update any CI → Set **AI Health Status = Unhealthy** → Incident is created.

---

## 🧪 Demo Scenarios

| CI Name | Health Status | Expected Result |
|---------|----------------|------------------|
| Web Server 01 | Unhealthy | Major Incident auto-created |
| DB Server Prod | Warning → Unhealthy | Impact summary + Incident |
| Email Gateway | Unhealthy | Incident + escalation |

---

## 🎯 Why This Project is Valuable

- Shows understanding of **CMDB**, **ITOM**, **AIOps**, **Incident Automation**  
- Demonstrates **AI-style reasoning** with no paid plugins  
- Perfect for interviews, LinkedIn portfolio, and GitHub showcase  
