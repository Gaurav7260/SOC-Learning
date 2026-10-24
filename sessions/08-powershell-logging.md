# Session 8 — PowerShell Logging and Suspicious Command Lines

## Key concepts
PowerShell is a legitimate administration and automation tool that attackers may also abuse. Review script content, execution context, parent process, and related telemetry rather than relying on one keyword.

- **PowerShell Event ID 4104:** Script Block Logging, when enabled.
- **Event ID 4103:** Module Logging, when enabled.
- **Sysmon Event ID 1:** process creation, if Sysmon is configured.
- **Windows Security Event ID 4688:** process creation; command-line capture depends on policy/configuration.

## Indicators worth reviewing
- `-EncodedCommand` / `-enc`
- `-WindowStyle Hidden`
- Unexpected parent process, e.g. a document editor launching PowerShell
- Suspicious script content or unexpected network activity

These are leads, not proof. Encoded commands and hidden windows can have legitimate uses.

## Simulated example
Timestamp: 2026-10-24 09:15:32; host: WORKSTATION-07; user: employee01; source: PowerShell 4104; parent: WINWORD.EXE; indicator: `-EncodedCommand`; network activity: not verified.

## Triage
1. Preserve the event and establish the exact timestamp/host/user.
2. Review available script-block content and process lineage.
3. Look for related 4688/Sysmon events and endpoint detections.
4. Correlate DNS, firewall, proxy, and identity records around the same time.
5. Record uncertainty and escalate according to the playbook if evidence warrants it.

## Quiz answer key
1. Word launching PowerShell with an encoded command is the strongest concern among the choices.
2. This does not prove compromise.
3. Check related process events, script content, user context, network activity, and endpoint alerts.
