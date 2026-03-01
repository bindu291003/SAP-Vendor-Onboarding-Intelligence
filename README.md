# SAP Vendor Onboarding Intelligence

AI-powered Single Agent system for automated vendor validation, risk assessment, duplicate detection, and SAP S/4HANA onboarding.

Live Demo: https://vendor-selector-clean-studio-53xl.architect.space

---

## 🚀 Project Overview

SAP Vendor Onboarding Intelligence is a production-ready MVP built using a **single orchestrator AI agent** integrated with SAP S/4HANA.

The system processes up to **four vendor submissions**, validates compliance, performs SAP duplicate checks, assigns risk levels, selects the most eligible vendor, and automatically creates the Business Partner in SAP using OData APIs.

This solution demonstrates enterprise AI orchestration without microservices, external databases, or overengineering.

---

## 🎯 Key Features

- Single Orchestrator AI Agent (No sub-agents)
- Multi-format input support (Manual, JSON, PDF, Word, Text)
- GST, PAN, and IFSC validation
- Missing field detection
- SAP duplicate vendor check
- Risk scoring (Low / Medium / High)
- Intelligent best-vendor selection (from 4 inputs)
- Automated SAP Business Partner creation
- Strict structured JSON output
- Clean Google-style minimal frontend UI

---

## 🏗 System Architecture

Frontend (React + Tailwind)  
↓  
Backend (Node.js / Express)  
↓  
Vendor_Onboarding_Agent (Single Lyzr Agent)  
↓  
SAP S/4HANA OData APIs  
↓  
Structured JSON Response  

All business logic is handled inside one single AI agent.

---

## 🔄 Workflow

1. User submits up to 4 vendors.
2. Agent extracts and normalizes data.
3. Agent validates GST, PAN, IFSC formats.
4. Agent checks missing mandatory fields.
5. Agent calls SAP Duplicate API.
6. Agent assigns risk level.
7. Agent selects the best eligible vendor.
8. If Approved → SAP Create Vendor API is triggered.
9. Structured JSON response is returned.

---

## 📦 JSON Output Format

The agent always returns:

```json
{
  "vendor_name": "",
  "gst_valid": true,
  "pan_valid": true,
  "bank_valid": true,
  "missing_fields": [],
  "duplicate_found": false,
  "risk_level": "Low | Medium | High",
  "final_decision": "Approved | Review | Rejected",
  "reason": "",
  "vendor_id": null,
  "confidence_score": 0.0
}
