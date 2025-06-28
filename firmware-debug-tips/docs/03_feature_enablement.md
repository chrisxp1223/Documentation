---
title: "System Feature Enablement Tips"
version: "v1.02"
date: "2025-02-14"
author: "AMD BIOS Engineering Team"
tags: ["firmware", "features", "security", "performance", "power"]
---

# ⚙️ System Feature Enablement Tips

This section outlines the enablement of key firmware features on AMD client platforms. It includes security, performance, thermal, and miscellaneous feature categories, along with their documentation references.

---

## 🔐 Security Features

### ✅ Prerequisites & Reference Materials

| Feature Level | Included Features |
|---------------|-------------------|
| **SCPC Level 1** | TPM, SVM, IOMMU, Secure Boot |
| **SCPC Level 2** | All Level 1 + DMAr, SecureBIO |
| **SCPC Level 3** | All Level 2 + SMM Isolation, DRTM, FAR, TSME |

| Feature | Technical Docs | Confluence / Training |
|--------|----------------|------------------------|
| TPM / SVM / IOMMU | #48882 IOMMU Spec | Secure Core PC - BIOS |
| DMAr | #56760 DMAr Implementation | |
| SecureBIO | #56560 Secure Biometrics BIOS Guide | |
| DRTM / SMM Isolation | #56896 DRTM Enablement Guide | |
| FAR | #55758 PSP BIOS Architecture Guide | 2022_FAR |
| RomArmor | #57380 RomArmor3 Guide | Rom Armor - BIOS |
| A/B Recovery | #56995 AB Recovery Design Guide | |
| RPMC | #56806 RPMC Key Spec | RPMC - BIOS Confluence |
| PSB | #56654 Secure Boot Enablement | PSB - BIOS Confluence |
| FMTC | #58216 FMTC Signing Process | FMTC Design |
| SPL | #55758 PSP BIOS Architecture Guide | SPL - BIOS |

---

## 🚀 Performance Features

| Feature | Docs | Training |
|--------|------|----------|
| Overclocking / EXPO | #58071 OC Programming Guide, #57251 EXPO Spec | Overclocking - Confluence |
| Windows Instrumentation | Microsoft Learn | |
| AMD Overclocking Drive | AMD OC Docs | |

---

## 🔋 Power Management & Thermal Features

| Feature | Docs | Confluence |
|--------|------|------------|
| Modern Standby | #56358 BIOS Implementation Guide | Modern Standby Debug Tips |
| Z State | ZSC_SOC_Arch_Spec | Z State - Confluence |
| DPTC / STT | #56095 DPTC App Note, #58036 Thermal Guide | STT / DPTC - BIOS Deep Dive |

---

## 🧩 Miscellaneous Features

| Feature | Docs | Notes |
|--------|------|-------|
| AIM-T | #57061 AIM-T Integration Guide | AIM-T 4.0 Debug |
| PMF | #58436 Smart PC Builder Guide, #57350 PMF Enablement Guide | PMF - BIOS Confluence |
| DDS (A+N) | Platform BIOS Implementation Guide | A+N Debug 20231124 |

---

> 📌 Please confirm feature readiness using aHDT or BIOS Setup options where applicable.