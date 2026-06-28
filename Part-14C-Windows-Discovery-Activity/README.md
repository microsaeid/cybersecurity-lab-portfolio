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
