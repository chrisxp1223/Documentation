---
title: "System Debug Logs Analysis Tips"
version: "v1.02"
date: "2025-02-14"
author: "AMD BIOS Engineering Team"
tags: ["debug", "log analysis", "bios", "firmware"]
---

# 📊 System Debug Logs Analysis Tips

This section introduces log interpretation strategies for various AMD firmware and hardware components. It focuses on insights gained from `aHDT`, CPU scan dumps, event logs, sleep study reports, and postcodes.

---

## 🧭 aHDT Log Prompt Overview

### 🏷 POSTCODE Info

- Use aHDT tool to decode postcodes or fall back to:
  - `BVM Postcode`
  - `postcode.txt` in UDC toolchain
  - `postcode.csv` in AGESA PI package
- Common source IDs:
  - `0x00` → On-chip Bootrom
  - `0x40` → ZSC
  - `0x50` → PMFW
  - `0xB0`, `0xB6`, `0xB8` → BIOS / AGESA / EDKII / USB

### 🔍 Firmware-Specific Status

- **MPASP / MP1 / MPIO**:
  - Use `MP*_PDEBUGPC`, `C2PMSG` to verify status or hang.
  - If aborted or stuck, take scan dump or RO CRU snapshot.
- **DF / UMC / Core**:
  - Confirm via CPU scan logs: look for ECC, HWA, HARDLOCK indicators.

---

## 🧪 CPU Scan Analysis

Validate DF, Core, UMC component behavior using scan IDs:
- Format: `ReportID: XXXX :: ScanID: YYYY`
- Example: HARDLOCK observed in core → check `LX3_PDEBUGPC`
- Cross-reference with DF assert or UMC parity errors

---

## 💤 Sleep Study Report Analysis

### Key Issues:

| Scenario | Symptom |
|----------|---------|
| **S0i3 Entry Blocked** | SW/DRIPS = 0% |
| **Low DRIPS** | Excessive idle events |
| **High Power** | WWAN/EC G-event every 8s |
| **Power Variability** | Fluctuating idle baseline |

- Use `powercfg /sleepstudy` and verify ACDC, abnormal shutdown
- Always pair with EC log for wake source correlation

---

## 🧾 Event Log Analysis

### Categories to Focus:

- **Bugcheck (BSOD)**  
  - Confirm via `MEMORY.DMP`, cross-check with AMDz

- **WHEA Events**  
  - Hardware error details (e.g., PCI vendor/device IDs)

- **TDR Errors**  
  - GPU Timeout Detection and Recovery

- **Unexpected Shutdown**  
  - Usually paired with Sleep Study or stress condition

- **Application Hang**  
  - GPU drivers or power-related app stalls

---
