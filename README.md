# SOC Learning — Sessions 1–10

A structured SOC Analyst L1 learning portfolio. Notes move from core concepts into Windows security telemetry and investigation. Exercises and included datasets are **simulated** unless explicitly labelled otherwise.

## Sessions
1. [Networking Foundations](sessions/01-networking-foundations.md)
2. [Introduction to SOC](sessions/02-introduction-to-soc.md)
3. [SOC Architecture and Lifecycle](sessions/03-soc-architecture-lifecycle.md)
4. [Security Data Sources](sessions/04-security-data-sources.md)
5. [Anatomy of a Security Event](sessions/05-anatomy-of-a-security-event.md)
6. [Windows Security Event IDs](sessions/06-windows-security-event-ids.md)
7. [Process Investigation](sessions/07-process-investigation.md)
8. [PowerShell Logging](sessions/08-powershell-logging.md)
9. [Windows Security Log Investigation](sessions/09-windows-security-log-investigation.md)
10. [Reading and Filtering Windows Event Logs](sessions/10-reading-filtering-windows-event-logs.md)

## Datasets
- [Simulated PowerShell events CSV](datasets/simulated_powershell_events.csv)
- [Session 9 simulated login events CSV](datasets/session-09-simulated-login-events.csv)

## Evidence and practice
- [Session 8 investigation report](evidence/session-08-investigation-report.md)
- [Session 9 investigation report](evidence/session-09-investigation-report.md)
- [Session 10 practical assessment report](evidence/session-10-practical-report.md)
- [Review questions and answers for Sessions 1–8](evidence/sessions-01-to-08-review-answers.md)

## Analyst principles
- An indicator is a lead, not proof of compromise.
- Correlate host, identity, process, network, and time context before conclusions.
- Record evidence, scope, uncertainty, actions, and escalation rationale.
- Use only authorized systems and safe, labelled datasets.
- Distinguish synthetic exercises from real endpoint evidence.

## Pending live-Windows practicals
These require access to a suitable Windows endpoint or remote lab and will be revisited later:
- Configure and validate Windows audit policies.
- Configure Sysmon and verify real event generation.
- Troubleshoot missing events and real endpoint telemetry collection.
- Test Sysmon collection end-to-end.

## Learning workflow
For each session: learn the core concepts, review examples and realistic scenarios, complete practical exercises, answer review questions, document evidence, and commit changes with a descriptive Git message. The next tool phase is planned to begin with Splunk and prepared Windows/Sysmon datasets.
