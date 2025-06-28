
---
title: "System Debug Tools Usage Tips"
version: "v1.02"
date: "2025-02-14"
author: "AMD BIOS Engineering Team"
tags: ["debugging", "firmware", "tools", "bios"]
---

# 🛠️ System Debug Tools Usage Tips

This section outlines the usage scenarios, download locations, and operation guidance for essential firmware-level debug tools on AMD client platforms.

---

## 🔧 UDC / PDT

- **Use Case**: Capture BIOS UART and postcode logs for system bring-up or issue reproduction.
- **Download**: AMD RMS → PDT Tools
- **Guide**: `20241022_UDC Card Training`

---

## 🐞 BIOSDBG

- **Use Case**: Source-level BIOS debugging with debug BIOS image.
- **Download**: AMD RMS → BIOSDBG
- **Guide**: `20241210_BIOSDBGV4_training`

---

## 📊 HDT / aHDS

- **Use Case**: Register inspection, CPU scan dump analysis.
- **Download**: AMD RMS / Internal Share
- **Guide**: `20231117_HDT and aHDS tool training`, `Scan Viewer`

---

## 🧮 aHDT

- **Use Case**: Stress condition debug, IP-level register trace.
- **Download**: Internal Share (e.g., hKysy/Kysy4)
- **Guide**: Refer to HDT/aHDS training materials

---

## 🎮 GDL

- **Use Case**: AMD GPU log capture and debug.
- **Download**: GDL Share Folder
- **Guide**: `GPUDebugLog_UserGuide.docx`

---

## 📥 aDebug

- **Use Case**: Analyze BSOD dump files, power state crashes.
- **Download**: Internal aDebug Share Folder
- **Guide**: `aDebugIntroduction-v068.pdf`

---

## 🧷 WinDbg

- **Use Case**: BSOD dump analysis, ASL tracing, driver inspection.
- **Download**: [WinDbg on Microsoft Store](https://apps.microsoft.com/store/detail/windbg/9PGJGD53TN86)
- **Guide**: `WinDbg Usage BKM.docx`

---

## 📝 System Log Collection

| Log Type         | Collection Method                                         |
|------------------|----------------------------------------------------------|
| **AMDz Log**      | `amdz.exe /saveall /savetxt`                             |
| **Event Log**     | `wevtutil.exe epl System system_log.evtx`               |
| **Battery Report**| `powercfg.exe /batteryreport`                            |
| **Sleep Study**   | `powercfg.exe /sleepstudy`                               |
| **Memory Dump**   | Check `C:\Windows\Minidump` or `C:\Windows\MEMORY.DMP`   |
| **BIOS Log**      | Captured via UDC or OEM method                           |
| **EC Log**        | Provided by ODM/OEM team                                 |

---

## 🔍 ETL & Trace Log Collection

| Trace Type       | Reference Document                 |
|------------------|-------------------------------------|
| **ETL Logs**      | `ETL Script usage SOP.docx`         |
| **USB Trace**     | `USB Trace log.pdf`                |
| **I2C Trace**     | `I2C Trace log.pdf`                |
| **eSPI Trace**    | `eSPI Trace log.pdf`               |
| **SPI Trace**     | `SPI Trace log.pdf`                |

---

> 📌 Use tools that match the platform AGESA version and toolchain release. Contact AMD BIOS Tooling Support if access is restricted.