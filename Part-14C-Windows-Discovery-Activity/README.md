# Part 14C — Windows Discovery Activity Monitoring

## Overview

This project documents a hands-on lab where I generated common Windows discovery activity and monitored the resulting events using Sysmon and Wazuh.

The objective was to understand how basic system and network discovery commands appear in endpoint telemetry and how they can be analyzed during a security investigation.

## Objectives

- Generate common Windows discovery activity using built-in command-line tools.
- Monitor endpoint events collected by Sysmon.
- Analyze related telemetry in the Wazuh dashboard.
- Understand how normal administrative commands can also appear during attacker reconnaissance.
- Practice documenting findings in a structured SOC investigation format.

- ## Lab Environment

| Component | Details |
|----------|---------|
| Host OS | Ubuntu Desktop 24.04 LTS |
| SIEM | Wazuh 4.14 |
| Endpoint | Windows 10 |
| Domain Controller | Windows Server 2022 |
| Monitoring Tool | Sysmon |
| Lab Type | Active Directory Home Lab |

## Investigation Steps

### Step 1 — Generate Windows Discovery Activity

On the Windows 10 endpoint, I executed several built-in Windows commands to generate discovery-related activity.

The following commands were executed:

```cmd
whoami
hostname
ipconfig
ping 8.8.8.8 -n 4
nslookup google.com
net user
net localgroup
net localgroup administrators
netstat -ano
tasklist
tasklist /svc
```

These commands generated Sysmon Process Create (Event ID 1) events that were forwarded to Wazuh for analysis.

## Detection Results

After executing the Windows discovery commands, Wazuh successfully detected and categorized the generated activity based on Sysmon Process Create (Event ID 1).

The investigation identified the following detection rules:

- **Rule 92031** – Discovery activity executed
- **Rule 92033** – Discovery activity spawned via PowerShell execution
- **Rule 92052** – Windows command prompt started by an abnormal process

These detections demonstrate how common Windows administrative commands can be monitored and analyzed during endpoint investigations.

### Threat Hunting Overview

![Threat Hunting Overview](screenshots/01-threat-hunting-overview.png)

### Rule 92031 – Discovery Activity Executed

![Rule 92031](screenshots/02-discovery-activity-rule-92031.png)

### Rule 92033 – Discovery Activity via PowerShell

![Rule 92033](screenshots/03-powershell-discovery-rule-92033.png)

### Rule 92052 – Command Prompt Started by an Abnormal Process

![Rule 92052](screenshots/04-command-prompt-rule-92052.png)

