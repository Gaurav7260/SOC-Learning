# Session 6 — Windows Security Event IDs

## Common Security log IDs
| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4634 | Logoff / session ended |
| 4648 | Logon attempted using explicit credentials |
| 4672 | Special privileges assigned to a new logon |
| 4688 | Process creation (command line requires appropriate policy/configuration) |
| 4720 | User account created |
| 4722 | User account enabled |
| 4728 | Member added to a global security group |
| 4732 | Member added to a local security group |
| 1102 | Security audit log cleared |

These events depend on OS version, audit policy, permissions, and collection configuration. An ID should be interpreted with its event fields and environment.

## Sysmon (if installed/configured)
- Event 1: process creation.
- Event 3: network connection, when enabled.
Sysmon is a separate telemetry source; its events do not appear unless Sysmon is installed and configured.

## Scenario
Sequence: multiple 4625 failures → 4624 success → 4672 privilege assignment. This is worth investigating, not automatic proof of compromise. Check account legitimacy, source, logon type, expected administrative duties, and subsequent process/network activity.

## Practice
For the sequence above, write: observed facts, hypotheses, missing evidence, and recommended next step. Keep facts separate from assumptions.
