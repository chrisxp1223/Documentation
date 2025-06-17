---
title: "System Firmware Bring-up Tips"
version: "v1.02"
date: "2025-02-14"
author: "AMD BIOS Engineering Team"
tags: ["firmware", "bring-up", "bios", "abl", "ec", "acpi"]
---

# 🧰 System Firmware Bring-up Tips

This section provides guidance and references for initializing AMD firmware, including BIOS and EC bring-up procedures. The goal is to ensure engineers can quickly set up a stable firmware baseline across AMD client platforms.

---

## 🔧 BIOS and EC Bring-up

### ✅ Prerequisites

Before performing any platform validation or firmware debugging, make sure the following technical documentation and reference materials are reviewed:

| Domain | Reference Title | Document ID / Link |
|--------|------------------|---------------------|
| **ABL** | AGESA™ PSP Bootloader Porting Guide | #55713 |
|        | Strix Point Platform BIOS Implementation Guide | `20231110_Strix Point` |
|        | Memory Training and ABL Config Training | `20231121` |
|        | ABL Logs Training | `2023_Abl_Logs_Training` |
|        | Confluence Page | ABL - BIOS (Client) |
| **SBIOS** | BIOS Porting Guide | #58224 |
|         | AGESA Interface Specification | #55483 |
|         | Common Platform Module Guide | #55730 |
| **ACPI** | ACPI v6.5 Porting Guidance | #58088 |
|         | AMD ACPI APMF Control Method Spec | #57295 |
|         | ACPI Notifications / Switchable Graphics | #63819 ~ #63821 |
| **EC** | Electrical Data Sheet (EDS) | #58158 |
|        | Platform EC Interface Spec | #56983 |
|        | Z State EC Implementation Notes | `20231117_Z State` |

---

### 📎 Bring-up Flow Highlights

The BIOS bring-up flow varies by platform but generally follows this pattern:

1. **PSP Bootloader & ABL Initialization**
   - Use AGESA™ PSP Bootloader Porting Guide to align firmware stages.
   - Validate all boot-related GPIO and strap configurations.
   
2. **Memory Training and Init**
   - Review memory topology and ensure alignment with ABL config.
   - Use `20231121_Memory Training` for fine-tuning.

3. **EC Co-Development**
   - Confirm EC firmware delivers proper power sequences (e.g., SLP_S3/S5, THERMTRIP).
   - Z State readiness must be verified with EC events.

4. **ACPI Table Definition**
   - Ensure proper generation of DSDT, SSDT, and APMF regions.
   - Use Microsoft’s Modern Standby documentation as needed.

---

## 🧪 Validation Tips

- Capture early postcodes and UART logs using **UDC/PDT**.
- Use **aHDT** to inspect status registers during POST, especially if hang is observed.
- Use **Scan Viewer** tools to cross-reference MP1/DF/UMC activity.

---

## 🛠 Recommended Tools for Bring-up

| Tool | Description | Source |
|------|-------------|--------|
| **UDC / PDT** | Capture postcodes & BIOS UART logs | RMS UDC/PDT Tools |
| **aHDT / aHDS** | System-wide status snapshot viewer | AMD Internal Tools |
| **BIOSDBG** | BIOS source-level debug interface | RMS BIOSDBG |
| **Scan Viewer** | Analyze CPU scan dumps | Available via aHDT integration |
| **WinDbg** | OS-level crash dump and driver debug | [Microsoft Learn](https://learn.microsoft.com/windows-hardware/drivers/debugger/) |

---

## 🧭 Reference Links (Internal)

- 🔗 [ABL BIOS Implementation - Confluence](https://amd.internal/abl-bios)
- 🔗 [AGESA BIOS Porting Guidance - PDF](https://amd.internal/guides/agesa-porting)
- 🔗 [Z State EC Flow Diagram](https://amd.internal/ec-zstate)
- 🔗 [BIOS Bring-up Checkpoints](https://amd.internal/bios-bringup-checklist)

> 📌 These links are only accessible to AMD internal staff. For external partners, equivalent guidance will be provided by your AMD liaison.

---