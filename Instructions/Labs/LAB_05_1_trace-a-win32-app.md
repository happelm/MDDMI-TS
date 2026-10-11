---
title: 'Lab 5.1 – Trace a Win32 app'
lab:
    title: 'Lab 5.1 – Trace a Win32 app'
    module: 'Day 2 – Apps, protect, support'
---

# Lab 5.1 – Trace a Win32 app

**Estimated time:** 45 minutes

**Goal:** Follow one Win32 app from the assignment to **Installed** – in the log, the registry and the portal.

1. Copy `cmtrace.exe`, `CmtraceInstall.ps1` and `CmtraceRemove.ps1` from the [Labfiles](https://github.com/happelm/MDDMI-TS/tree/main/Labfiles) into one folder and package it with the [Microsoft Win32 Content Prep Tool](https://github.com/microsoft/Microsoft-Win32-Content-Prep-Tool) (`IntuneWinAppUtil.exe`), setup file `CmtraceInstall.ps1`.
2. Intune admin center → Apps → Windows: add a **Windows app (Win32)** `etcX-CMTrace` with these settings and assign it as **Required** to `studentXdevices`:

   | Setting | Value |
   |---|---|
   | Install command | `PowerShell.exe -ExecutionPolicy Bypass -File "CmtraceInstall.ps1"` |
   | Uninstall command | `PowerShell.exe -ExecutionPolicy Bypass -File "CmtraceRemove.ps1"` |
   | Install behavior | System |
   | Detection rule | File: `C:\Windows`, file or folder `CMTrace.exe`, file or folder exists |

3. CL3, elevated PowerShell: restart the IME, then follow `AppWorkload.log` in CMTrace.

   ```powershell
   Restart-Service -Name IntuneManagementExtension
   ```

4. Find the stages from the lifecycle slides in `AppWorkload.log`: policy received, download, install, detection, state reported.
5. CL3: `regedit` → `HKLM\SOFTWARE\Microsoft\IntuneManagementExtension\Win32Apps` – find the key of `etcX-CMTrace` and its state.
6. Intune admin center: compare the install status of `etcX-CMTrace` on CL3 with what the log says.

### Checkpoint

- [ ] Download, install and detection of `etcX-CMTrace` found in `AppWorkload.log`
- [ ] App key and state message found in the registry
- [ ] Portal shows **Installed** for CL3

**Note:** Under `Win32Apps`, apps assigned to the device sit under the all-zeros GUID, apps assigned to a user under that user's Entra object ID.

**Why:** The detection rule decides **Installed** – not the exit code alone. When the portal and the log disagree, the log is right.
