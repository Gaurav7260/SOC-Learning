# Session 10 — Reading and Filtering Windows Event Logs

## Objectives
- Understand common event fields and why they matter.
- Filter large log collections to the records relevant to a question.
- Correlate authentication and process-creation events.
- Separate evidence from hypotheses and recognize telemetry limitations.

## Common fields
| Field | Meaning |
|---|---|
| `TimeCreated` | Event timestamp |
| `Computer` | Device that recorded the event |
| `EventID` | Event type identifier |
| `TargetUserName` | Account involved in an event, when present |
| `IpAddress` | Recorded source address, when present |
| `LogonType` | Type of logon for relevant authentication events |
| `Status` / `SubStatus` | Authentication status or failure reason, when available |
| `ProcessName` / `NewProcessName` | Process-related fields, depending on provider and event |
| `CommandLine` | Process command line, if captured and available |
| `ParentImage` | Parent process image in relevant Sysmon records |

Field names and availability vary by event provider, event version, export format, and audit/configuration settings. Do not assume every event contains every field.

## Why filter?
Filtering narrows a large set of records to the events relevant to an investigation. An analyst might filter Event ID 4625, restrict the time range, group by account/source, and then compare nearby 4624 records. Process investigation may include Security Event ID 4688 and Sysmon Event ID 1.

Filtering is not proof of an attack. It is a way to focus analysis.

## Common examples
- Repeated failures: filter 4625 and examine time, account, host, and source.
- Failure followed by success: correlate 4625 and 4624, then inspect logon details and post-authentication activity.
- Process activity: inspect 4688 or Sysmon Event ID 1; check image, parent process, user, timestamp, and command line where available.
- Missing expected records: consider audit policy, event filtering, retention/rollover, permissions, forwarding, and collection health.

## Practical scenario
Simulated records show three 4625 failures for account `alex` on `WS-04`, followed by a 4624 success from the same recorded source IP. Two 4688 process-creation records follow; the command line is unavailable.

### Supported observations
- Three failed logons are recorded before one successful logon.
- Two process-creation events follow.
- The command line is missing from the supplied data.

### Hypotheses and unknowns
The sequence could be suspicious, but it does not establish compromise. The analyst does not yet know whether the logon was expected or what PowerShell was instructed to do.

### Next steps
Validate the logon context and source; obtain process command line and parent process if available; correlate endpoint, identity, and network telemetry; follow the escalation playbook.

## Key reminders
- Event ID alone is not enough to determine intent.
- A recorded account is not proof of a specific human's identity.
- Process creation does not by itself prove a malicious script completed successfully.
- Missing telemetry does not prove that activity did not happen.
- State observations, hypotheses, unknowns, and next steps separately.

## Practical and assessment
- Practical score: 4/4.
- Quiz: pending learner completion.
- Dataset status: synthetic training records.
