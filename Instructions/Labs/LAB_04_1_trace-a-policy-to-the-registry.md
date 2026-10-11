---
title: 'Lab 4.1 – Trace a policy to the registry'
lab:
    title: 'Lab 4.1 – Trace a policy to the registry'
    module: 'Day 1 – Method, enroll, configure'
---

# Lab 4.1 – Trace a policy to the registry

**Estimated time:** 30 minutes

**Goal:** Follow one user setting and one device setting from the portal through the SyncML stream into the registry.

1. CL3: start `SyncMLViewer.exe` from the [Labfiles](https://github.com/happelm/MDDMI-TS/tree/main/Labfiles) and leave it running.
2. Intune admin center → Devices → Manage devices → Configuration → Create → New policy → Windows 10 and later → Settings catalog. Create two policies:
   - `etcX-User`: one setting marked **(User)**, assigned to `studentXusers`
   - `etcX-Device`: one setting marked **(Device)** plus Config Refresh (enabled, cadence 30 minutes), assigned to `studentXdevices`
3. CL3: sync (Settings → Accounts → Access work or school → your account → Info → Sync) and find both values in the SyncML stream.
4. CL3, elevated: `regedit` → `HKLM\SOFTWARE\Microsoft\PolicyManager\current` – find both values.
5. Intune admin center: open both policies and check the per-setting status for CL3.

### Checkpoint

- [ ] Both settings visible in SyncML Viewer
- [ ] Device setting under `HKLM\SOFTWARE\Microsoft\PolicyManager\current\device`
- [ ] Both policies **Succeeded** on CL3

**Note:** `PolicyManager\providers\<GUID>\default\Device\<area>` holds the values Intune sent – the GUID is your enrollment GUID from Lab 3.1. `PolicyManager\current\device` holds the merged result that Windows applies.

**Why:** The sync status in the portal is a service view. The registry shows what the device actually applied.

