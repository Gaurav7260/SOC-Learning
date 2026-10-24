# Review Answers — Sessions 1–8

These are concise review answers based on the concepts covered. For earlier sessions, some prompts are reconstructed from the learning topics rather than presented as verbatim historical quiz transcripts.

## Session 1 — Networking
- MAC is a link-layer identifier used on a local network; IP is a logical address used for routing.
- DNS and firewall logs can be correlated to connect a name lookup with a connection attempt.
- The default gateway routes traffic to destinations outside the local subnet.
- OSI layers help analysts reason about link, network, transport, and application evidence.

## Session 2 — SOC
- Event = recorded activity; alert = detection notification; incident = credible/confirmed security case requiring coordinated handling.
- Failed logins followed by a success are suspicious but need context and corroboration.
- L1 validates alerts, gathers context, follows playbooks, documents, and escalates.

## Session 3 — Lifecycle
- A SIEM collects/normalizes data and runs analytics; alerts need analyst triage.
- Correlate by timestamp, user, host, source IP, process, and domain.
- High failure counts are a detection lead, not proof by themselves.

## Session 4 — Data sources
1. Windows authentication logs record logon-related events; EDR alerts flag suspicious endpoint behaviour.
2. DNS shows requested names/responses; firewall telemetry helps establish whether related traffic was attempted, allowed, or blocked.
3. Correlation connects events across sources using shared attributes.
4. Suspicious does not equal proven malicious; validate context.

## Session 5 — Event anatomy
Useful fields include timestamp, host, account, source/destination, provider/event ID, action/result, process, severity, and message. Availability varies.

## Session 6 — Event IDs
- 4624 success; 4625 failure; 4688 process creation; 1102 audit log cleared.
- 4672 means special privileges were assigned; it is not inherently malicious.
- Event sequences should be checked against source, logon type, expected activity, and subsequent actions.

## Session 7 — Process investigation
- Parent-child relationships show execution lineage.
- Check process path, command line, user, IDs, timestamp, hash/signer where available, and related network/EDR events.
- Never execute unknown files merely to test a suspicion.

## Session 8 — PowerShell
1. Word launching PowerShell plus an encoded-command indicator is the strongest concern.
2. The indicator alone does not prove compromise.
3. Check process events, script content, user context, network activity, and endpoint alerts.

## Safe-practice reminder
Use only authorized systems. Label simulated data clearly. Do not visit malicious URLs, run unknown scripts, or upload private logs to public repositories.
