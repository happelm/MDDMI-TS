---
title: 'Lab 0.1 – Set up your lab'
lab:
    title: 'Lab 0.1 – Set up your lab'
    module: 'Day 1 – Method, enroll, configure'
---

# Lab 0.1 – Set up your lab

**Estimated time:** 20 minutes

**Goal:** Bring CL3 and CL4 into the training tenant and into your device group, named so that everybody can find them.

1. Look up your user `etcX` and your number X in `course.txt` from the trainer.
2. CL3 and CL4 start at OOBE. Rename them to `CL3-yourname` and `CL4-yourname` before you join them: press `Shift+F10` in OOBE and run the command below, then let the client restart.

   ```powershell
   powershell -Command "Rename-Computer -NewName 'CL3-yourname' -Restart"
   ```

3. Finish OOBE on both clients and join them to Microsoft Entra ID with `etcX` (work or school account).
4. Entra admin center → Groups → `studentXdevices` → Members: add `CL3-yourname` and `CL4-yourname`.
5. From now on, every object you create in the tenant starts with `etcX-`.

### Checkpoint

- [ ] `dsregcmd /status` on CL3 and CL4: `AzureAdJoined : YES`
- [ ] Both devices listed in Intune admin center → Devices → Windows
- [ ] Both devices are members of `studentXdevices`

**Note:** A computer name has at most 15 characters – shorten `yourname` if needed. Your roles only reach devices whose name matches the lab naming pattern, so keep the `CL3-` / `CL4-` prefix.

**Why:** Every assignment in the following labs targets `studentXdevices` or `studentXusers`. A device that is not in your group gets nothing.
