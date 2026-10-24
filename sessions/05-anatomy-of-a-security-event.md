# Session 5 — Anatomy of a Security Event

## Useful fields
- Timestamp and time zone
- Hostname/device ID
- Username or account identifier
- Source and destination IP
- Event ID/provider
- Process name, path, command line, and parent process when available
- Action/result (success, failure, allowed, blocked)
- Severity, rule name, and message

Fields differ by source and may be missing. Normalize timestamps before correlating records.

## Example: failed Windows logon
A 4625 event can include the target account, logon type, source/workstation details, failure status/substatus, and timestamp. Field availability depends on Windows version, event configuration, and event rendering.

## Triage checklist
1. What happened, and when?
2. Which user and device are involved?
3. Was the action successful?
4. Is the source expected for this user/device?
5. Are there related events before or after it?
6. What is known, unknown, and the next safe check?

## Practice
Create a short event summary from a fictional failed login. Include timestamp, account, host, source, result, evidence still needed, and a cautious assessment. Never present invented values as real telemetry.
