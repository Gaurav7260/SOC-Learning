# Session 9 — Investigation Evidence Report

## Case summary
**Scenario:** Multiple failed logons followed by a successful logon  
**Dataset:** `datasets/session-09-simulated-login-events.csv`  
**Data classification:** Synthetic training records; not real endpoint evidence  
**Host:** WORKSTATION-12  
**Account:** user02

## Observed evidence
- Four Event ID 4625 records occur between 10:21:01 and 10:21:10.
- One Event ID 4624 record occurs at 10:21:15.
- The supplied records show the same account, host, and documentation-only source IP (198.51.100.24).

## Initial assessment
The sequence warrants investigation because repeated failed authentication is followed by success. It does not, by itself, establish brute force, account compromise, or the identity of the person operating the account.

## Recommended follow-up
1. Inspect successful and failed logon details, including logon type and status/substatus where available.
2. Validate the source IP and whether it is expected for this account and environment.
3. Review identity, VPN, remote-access, and endpoint telemetry for the same time window.
4. Look for process creation, privilege use, additional logons, and network activity after the successful logon.
5. Escalate according to the playbook if evidence or risk warrants it; document unresolved questions.

## Limitations
The dataset contains only a small set of simulated fields. It has no real user validation, full event XML, authentication context, or post-login telemetry. Conclusions must remain limited to the supplied records.

## Analyst conclusion
**Disposition:** Continue investigation; compromise not confirmed.  
**Rationale:** Repeated failures followed by success are observable, but more context is required to distinguish suspicious activity from legitimate authentication errors.
