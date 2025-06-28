
---
title: “System Debug Tips”
version: “v1.02”
date: “2025-02-14”
author: “AMD BIOS Engineering Team”
tags: [“debug”, “firmware”, “bios”, “troubleshooting”]
---

# 🧩 System Debug Tips

This section provides practical tips for debugging firmware-related issues across AMD client platforms. These checklists and references are intended to help identify the issue domain, understand ownership, and gather proper evidence for triage.

---

## 🔍 System Debug Guidelines

### 🪛 First-Level Checks
- **Refer to internal guide**: “First Level Debug System in Farm Side”
- **Checklist**:
  - System boots to OS?
  - Any visible postcode stuck?
  - BIOS/EC version validated?
  - Did the issue reproduce under stress/power cycling?

---

## 👤 Component Ownership

Refer to the Program Ownership Confluence page to verify ownership for the relevant subsystem:
- BIOS
- EC
- PSP
- MP1/MP2
- GFX/IMU
- NBIO/DXIO/MPIO
- SMU

---

## 🧬 Boot Flow References
- **Download and reference the latest PDF**: Strix_Bootflow_Sequence.pdf
- **Covers**:
  - Pre-boot stages (ROM → ABL → BIOS)
  - SMU / PSP handshakes
  - Entry points for S0i3 / Modern Standby

---

## 📁 Boot Logs
- **Compare logs with CRB baseline**:
  - CRB Report Logs for standard PI version
  - Stress Test Logs on Korat+ CRB with Krackan APU

**Check for**:
- Missing SMU/MP1 handshakes
- Unexpected postcode hangs
- Platform resets or WDT triggers

---

> 📌 Up next: 06 - System Debug Logs Analysis Tips
