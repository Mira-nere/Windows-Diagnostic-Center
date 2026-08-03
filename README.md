# Automated Windows System Maintenance & Monitoring Framework

A HomeLab & Foundational-ready, background-automated PowerShell maintenance framework for Windows environments. This project automates daily housekeeping, weekly diagnostic scans, and monthly health auditing using native Windows utilities, Task Scheduler triggers, and structured logging.

IT Home Laboratory Project 1:  Supplementary for Help Desk Support and Administrators. <br>
Specialized in Windows-featured Diagnostic Features.
**---**

**Learning Objectives:**

Windows Architecture

Windows Administration
- Computer Management
- Task Manager
- Resource Monitor
- Performance Monitor
- Reliability Monitor
- Event Viewer
- Services.msc
- Task Scheduler
- Device Manager

Microsoft Sysinternals
- Process Explorer
- Autoruns
- TCPView
---

# Project Overview

Maintaining system health, disk space, and security across Windows workstations often requires repetitive manual intervention. This project automates essential IT system administration tasks using lightweight, zero-dependency PowerShell scripts.

By running silently in the background via **Windows Task Scheduler**, the framework ensures optimal system performance, automated log tracking, proactive malware scanning, and early detection of battery or storage degradation.

---

# Key Features & Execution Cadence

### 📅 Daily Maintenance
* **Temporary Files Cleanup:** Automatically purges temporary files from `%TEMP%`, `%SystemRoot%\Temp`, and Prefetch folders to prevent disk bloat.
* **Recycle Bin Emptying:** Silently clears the Windows Recycle Bin for all local drives without user prompts (`Clear-RecycleBin -Force`).

### 📅 Weekly Maintenance
* **Storage Space Auditing:** Calculates available C: drive capacity (GB and % free) and appends timestamped health alerts to `MaintenanceLogs.txt`.
* **System File Integrity (SFC):** Executes `sfc /scannow` to detect and repair corrupted Windows system files.
* **Component Store Repair (DISM):** Runs `DISM /Online /Cleanup-Image /RestoreHealth` to repair underlying Windows system images.
* **Quick Antivirus Scan:** Initiates a Microsoft Defender quick scan (`Start-MpScan -ScanType QuickScan`) to maintain baseline malware protection.

### 📅 Monthly Maintenance & Auditing
* **Battery Health & Capacity Logging:** Generates a detailed HTML battery report via `powercfg /batteryreport` and logs battery degradation metrics (Full Charge vs. Design Capacity).
* **Deep Antivirus Scan:** Executes a thorough Microsoft Defender full scan (`Start-MpScan -ScanType FullScan`) during scheduled off-peak hours.

---

