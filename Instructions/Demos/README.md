# Demos – overview

Trainer demos and setup checklists for the trainer pod in `smart.etc`. Participants work on CL3/CL4 only; everything here is shown by the trainer. Scripts are in [`Labfiles/Demos`](https://github.com/happelm/MDDMI-TS/tree/main/Labfiles/Demos).

| Demo | Devices | Shows | Needs |
|---|---|---|---|
| [Hybrid join and Microsoft Entra Kerberos](hybrid-join-entra-kerberos.md) | CL1/CL2 | Microsoft Entra hybrid join without computer sync, Windows Hello cloud Kerberos trust, SSO to `\\dc1\labfiles` | DC1 on Windows Server 2025, co-management workloads on Intune |
| [Azure Files share and Microsoft Entra Kerberos](azure-files-entra-kerberos.md) | CL3/CL4 | SSO to `\\mddmi.file.core.windows.net\labfiles` through Microsoft Entra Kerberos, without line of sight to DC1 | Setup checklist only after a rebuild |
| [MDM wins over GP demo](mdm-wins-over-gp-demo.md) | CL1 | GPO-01 and Intune set the same SmartScreen setting; registry and event log show which side wins | Hybrid join demo set up, GPO-01 link enabled for the demo |

**Order:** set up the hybrid join demo first; the MDM wins over GP demo builds on it.
