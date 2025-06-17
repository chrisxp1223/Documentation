---
title: "Firmware Debug Tips"
version: "v1.02"
date: "2025-02-14"
author: "AMD BIOS Engineering Team"
tags: ["firmware", "debug", "amd", "bios", "tools"]
---

# 📘 Introduction

This document provides a comprehensive collection of debugging tips for AMD client firmware. It is intended for firmware and BIOS engineers working on system bring-up, issue triage, feature enablement, and root cause analysis across AMD platforms.

All tips included in this document are compiled from real-world scenarios observed during internal validation and customer support engagements.

---

## 📌 Purpose

The main goals of this document are:

- To provide a centralized reference for firmware-level debugging techniques.
- To assist engineers in narrowing down system-level issues by disabling/enabling specific firmware features.
- To document best practices for using AMD and third-party debug tools.
- To summarize typical platform behaviors, log interpretations, and mitigation patches.

---

## 🧭 Scope

This guide covers the following categories:

- **System Firmware Bring-up Tips**  
  Steps and references for initial BIOS and EC validation.

- **Feature Enablement Tips**  
  Security, performance, and power features and how to enable/verify them.

- **Debug Tool Usage**  
  Overview of internal tools like UDC, BIOSDBG, aHDT, WinDbg, and more.

- **System Debug & Log Analysis**  
  Techniques for interpreting logs, postcodes, and trace data during failures.

- **Platform-Specific Patches**  
  Temporary firmware modifications to isolate root causes (e.g., disabling WDT, Sync Flood, IOMMU, etc.)

---

## 📎 Revision History Summary

| Date       | Version | Notes                                                                 |
|------------|---------|------------------------------------------------------------------------|
| 2024-12-09 | 1.00    | Initial release. Covers basic feature toggling and debugging scenarios |
| 2024-12-31 | 1.01    | Added tips: Disable CF9 Reset, GPIO Interrupts, CPPC, and more         |
| 2025-02-14 | 1.02    | Expanded with bring-up flow, feature categories, and tool usage        |

---

## 📂 Target Audience

This documentation is intended for:

- AMD BIOS/firmware developers
- ODM/OEM firmware engineers
- Platform debug and validation teams
- Customer engineering support roles

---

## 📌 Notes

> All patches referenced in this document are verified on the **StrixKrackanPI** BIOS and tested on **Korat+ CRB** with **Krackan APU**.  
> Some feature toggles are applied via **APCB tokens** or **PCD values** and may not be accessible via CBS (Configurable BIOS Settings).

---

## 🔗 Related Resources

- AMD UDC & PDT Documentation
- AGESA Porting Guides
- Windows Debugging Tools (WinDbg)
- Platform BIOS Implementation Guides
- AMD Secure Core PC Enablement Guide

---