# Session 7 — Process Investigation

## Why process lineage matters
A process is a running program. Parent-child relationships show what launched it and can reveal unusual execution chains. Legitimate tools can be abused, so process names alone are weak evidence.

## Fields to inspect
- Image / process path
- CommandLine
- ParentImage / parent process
- ProcessId and parent process ID
- User
- Hashes, when collected
- Timestamp / UtcTime
- Hostname and related network events

## Telemetry
Windows Event ID 4688 can record process creation; command lines may require an audit policy setting. Sysmon Event ID 1 can provide richer process creation data when installed and configured.

## Scenario
A document editor launches PowerShell, which launches an unknown executable, followed by an unexpected outbound connection. Investigate the parent-child chain, command line, signer/hash/reputation, user context, file origin, and related network/EDR events.

## Practice
Given a fictional process chain, list three benign explanations and three checks that would increase confidence in a malicious hypothesis. Do not execute unknown files to test them.
