---
title: "Platform Patch Reference Tips"
version: "v1.02"
date: "2025-02-14"
author: "AMD BIOS Engineering Team"
tags: ["firmware", "patch", "bios", "platform debug"]
---

# 🛡️ Platform Patch Reference Tips

This section provides reference patches used to isolate or resolve platform-level issues during firmware bring-up, validation, and debug. Each patch includes conditions for use, implementation notes, and verification steps.

---

## 🔧 Disable WDT (Watchdog Timer)

- **When to Use**:  
  If `s5_reset_status BIT25 = 1` in aHDT log (watchdog issuereset), disable CPU, FCH, and DF WDT to prevent system resets during debugging.

- **Patch Scope**:  
  - Disable CPU WDT via `CpuWdtCfg BIT0 = 0`
  - Disable FCH WDT via `watchdogcontrol BIT3 = 1`
  - Disable DF WDT via `DfGlobalCtrl BIT5:4 = 3`

- **How to Confirm**:  
  Check values in aHDT or aHDS logs via register viewer or green box overlays.

---

## ❌ Disable Sync Flood

- **When to Use**:  
  If `s5_reset_status BIT27 = 1` indicating sync flood reset triggered.

- **Patch Scope**:  
  - Disable Sync Flood Reset and Config in FCH and DF registers.

- **Verification**:  
  aHDS:  
  - `acpiconfig BIT18 = 0`  
  - `AB MiscCtl2 BIT2 = 0`  
  - `PIEConfig BIT19 = 1`  
  - `CoherentSlaveConfigA0 BIT24 = 1`

---

## 🚫 Disable CF9 Reset

- **When to Use**:  
  If `s5_reset_status BIT18/19/20 = 1`, indicating unexpected CF9 trigger.

- **Patch Scope**:  
  - Set `cf9rstdisable = 1` at Exit Boot Services.

- **Confirmation**:  
  aHDS register:  
  - `pmiodebug BIT6 = 1`

---

## 🧯 Disable SMM Supervisor

- **When to Use**:  
  Debugging issues potentially related to SCPC Level 3 or SMM handler.

- **Patch Scope**:  
  - Override CBS values to prevent enabling SMM Supervisor.

- **Confirmation**:  
  - Absence of `B0005XXX` SMI postcodes in UDC logs.

---

## 🔌 Disable GPIO Interrupts

- **When to Use**:  
  BSOD 0x133 or Interrupt Storms (e.g., AGPIO29)

- **Patch Scope**:  
  - Disable specific GPIOs used for wake/interruption (e.g., TOUCHPAD_INT)

- **Confirmation**:  
  - Serial log output of GPIO init  
  - aHDS: `spi_tpm_cs_l_agpio29 BIT12 = 0`

---

## 🧪 Disable/Enable Device D3 Cold

- **Use Case**:  
  To validate power-related issues (e.g., device fails in low power state)

- **How To**:  
  - Toggle via PBS setup: Power Saving Config > NVME D3 Cold

- **Confirmation**:  
  - ECRAM dump: Offset 0xB7 BIT4/5

---

> 📘 For full patching scenarios, refer to Section 8 of the full document or apply context-specific patches only after confirming system logs.
