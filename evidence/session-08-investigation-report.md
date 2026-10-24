# Session 8 — Investigation Report

**Dataset classification:** Simulated training data; not collected from a real endpoint.  
**Status:** Initial triage; compromise not established.

## Observed
- Time: 2026-10-24 09:15:32 (timezone not specified in the sample).
- Host: WORKSTATION-07.
- User: employee01.
- PowerShell-related event: 4104.
- Parent process reported: WINWORD.EXE.
- Command-line indicator: `-EncodedCommand`.
- Network activity: not verified.

## Assessment
A document editor associated with PowerShell and an encoded-command indicator is suspicious enough to investigate. The sample lacks decoded script content, process IDs, file/hash details, identity context, and corroborating network telemetry. No conclusion of compromise is justified from these fields alone.

## Next steps
1. Confirm source logs, time zone, and whether Script Block Logging was enabled.
2. Review complete script-block content in an authorized environment.
3. Correlate process creation and parent-child events.
4. Review EDR, DNS, proxy, and firewall events near the timestamp.
5. Check whether the user was performing an approved workflow.
6. Document evidence and escalate according to the organization's playbook.

## Disposition
**Unconfirmed / needs more evidence.** This is a simulated exercise and no response action was taken.
