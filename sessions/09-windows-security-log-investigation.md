# Session 9 — Windows Security Log Investigation: From Events to Evidence

## Objectives
- Correlate authentication events by time, account, host, and source IP.
- Separate recorded observations from hypotheses.
- Identify the next evidence needed before deciding whether to close, continue, or escalate an alert.

## Core concepts
An investigation asks what the records show, when activity occurred, which account and device were involved, and whether the activity warrants further investigation. Event correlation connects related records, but correlation alone does not prove malicious intent.

Useful Windows Security Event IDs:
- **4624** — successful logon.
- **4625** — failed logon.
- **4634** — logoff/session ended.
- **4648** — logon attempted using explicit credentials.
- **4672** — special privileges assigned to a new logon.
- **4688** — process creation; command-line data depends on audit configuration.
- **1102** — Security audit log cleared.

## Practical dataset
The included `datasets/session-09-simulated-login-events.csv` is a synthetic training dataset. Its IP address is from the documentation-only range 198.51.100.0/24; the records are not real authentication evidence.

The sequence contains four failed logons followed by a successful logon for account `user02` on `WORKSTATION-12`, all attributed in the records to the same source IP.

## Investigation approach
1. Confirm the time range and host/account scope.
2. Count failures and identify whether they share account, host, and source attributes.
3. Inspect the successful logon's details, including logon type, workstation, authentication package, and status fields where available.
4. Validate whether the source and activity are expected for the user and environment.
5. Review activity after authentication: process creation, privilege use, remote access, and network telemetry where available.
6. Record facts separately from hypotheses; escalate according to the incident playbook when evidence warrants it.

## Evidence vs hypothesis
- **Observation:** Four failed logon events are followed by one successful logon event in the supplied records.
- **Hypothesis:** The sequence could reflect password guessing or an ordinary user who mistyped a password.
- **Unknown:** Whether the successful logon was authorized, who operated the account, and what happened afterward.
- **Next steps:** Validate source legitimacy and logon context; correlate additional endpoint and identity telemetry.

An account name does not prove the identity of the person using it. A sequence of failed logons followed by success is a lead, not proof of compromise.

## L1 disposition
Do not automatically close the alert because a login succeeded, and do not declare compromise based on this sequence alone. Continue investigation or escalate based on evidence and the organization's playbook, documenting uncertainty.

## Completion
- Practical: passed all three exercises.
- Quiz: 4/4 (100%).
- Dataset status: synthetic/simulated.
