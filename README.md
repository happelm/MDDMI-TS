# MDDMI-TS – Troubleshooting Microsoft Intune

Lab instructions for the MDDMI-TS troubleshooting workshop.

- **Read online:** <https://happelm.github.io/MDDMI-TS/>

## Labs

| Lab | Title | Time |
|---|---|---|
| 0.1 | [Set up your lab](Instructions/Labs/LAB_00_1_set-up-your-lab.md) | TBD |
| 2.1 | [Collect and read Intune logs](Instructions/Labs/LAB_02_1_collect-and-read-intune-logs.md) | TBD |
| 3.1 | [Check the enrollment state](Instructions/Labs/LAB_03_1_check-the-enrollment-state.md) | TBD |
| 4.1 | [Trace a policy to the registry](Instructions/Labs/LAB_04_1_trace-a-policy-to-the-registry.md) | TBD |
| 5.1 | [Trace a Win32 app](Instructions/Labs/LAB_05_1_trace-a-win32-app.md) | TBD |
| 6.1 | [Trace a platform script](Instructions/Labs/LAB_06_1_trace-a-platform-script.md) | TBD |
| 8.1 | [Web sign-in and cloud Kerberos](Instructions/Labs/LAB_08_1_web-sign-in-and-cloud-kerberos.md) | TBD |

### Appendix

[Log map](Instructions/Appendix.md)

## About this guide

Each lab lists its goal, the steps at task level (not every click) and a checkpoint you confirm before moving on.

- **Steps** say what to do and where. Menu paths use → between levels.
- **Checkpoint** items are the definition of done. If one fails, tell the trainer before you continue.
- **Troubleshooting scenarios** start with a symptom. Use the hints in order and open the solution only after you have a root cause and evidence.

### Your lab environment

You work with two Windows 11 clients and one account in the trainer's training tenant. Your clients join Microsoft Entra ID natively and enroll in Intune – no domain join, no Configuration Manager.

| System | Role | Your part |
|---|---|---|
| CL3, CL4 | Windows 11, your lab clients | Rename to `CL3-yourname` and `CL4-yourname`, join to Entra ID, enroll in Intune |
| DC1, SRV1 | On-premises domain `smart.etc` in the classroom network | Provided by the trainer – target for resource access with Microsoft Entra Kerberos |
| Tenant | Trainer's training tenant | Sign in with your account `etcX` |

X is your participant number from the trainer.

### Accounts and groups

| Name | Type | Used for |
|---|---|---|
| `etcX` | User account in the training tenant | Your sign-in on CL3/CL4 and in the admin centers |
| `studentXdevices` | Existing Entra group | Your devices – add CL3 and CL4 |
| `studentXusers` | Existing Entra group | Your user |

Passwords are handed out by the trainer.

### Tools

- CMTrace for all .log files – Intune Management Extension logs in `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`
- Intune admin center: intune.microsoft.com · Entra admin center: entra.microsoft.com

## Known issues and feedback

Known issues, workarounds and corrections are tracked in the [Issues](https://github.com/happelm/MDDMI-TS/issues) tab. If something in a lab does not work as described, check the open issues first, then open a new one with the lab number and the step.
