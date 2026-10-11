---
title: 'Lab 8.1 – Web sign-in and cloud Kerberos'
lab:
    title: 'Lab 8.1 – Web sign-in and cloud Kerberos'
    module: 'Day 2 – Apps, protect, support'
---

# Lab 8.1 – Web sign-in and cloud Kerberos

**Estimated time:** 45 minutes

**Goal:** Sign in with web sign-in and reach on-premises and Azure Files resources without a password prompt.

1. Intune admin center → Devices → Manage devices → Configuration → Create → New policy → Windows 10 and later → Settings catalog: policy `etcX-WebSignIn`, Authentication → **Enable Web Sign In** = Enabled, assigned to `studentXdevices`.
2. CL4: sync, sign out and sign in again with web sign-in and your existing MFA.
3. Settings catalog policy `etcX-WHfB`, assigned to `studentXdevices`: Windows Hello for Business → **Use Windows Hello For Business** = true and **Use Cloud Trust For On Prem Auth** = Enabled. Set up Windows Hello on CL4 and sign in with it.
4. CL4: open a share on SRV1 in `smart.etc` (path from the trainer).
5. CL4: check the SSO state and your tickets.

   ```cmd
   dsregcmd /status
   ```

   ```cmd
   klist
   ```

6. CL4: connect to the Azure file share provided by the trainer.

### Checkpoint

- [ ] Web sign-in works on CL4
- [ ] `dsregcmd /status`: `AzureAdPrt`, `CloudTgt` and `OnPremTgt` are `YES`
- [ ] `klist` shows a ticket for SRV1
- [ ] Azure file share opens without a password prompt

**Note:** Web sign-in requires Windows 11 22H2 with KB5030310 or later and is not supported on hybrid or domain-joined devices. `CloudTgt` is the cloud Kerberos ticket for cloud resources, `OnPremTgt` the one for on-premises resources.

**Why:** No PRT, no SSO. Always start with `dsregcmd /status` before you look at the network or the file server.
