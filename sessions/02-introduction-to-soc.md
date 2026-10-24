# Session 2 — Introduction to a SOC

## What is a SOC?
A Security Operations Center monitors security telemetry, detects suspicious activity, investigates alerts, coordinates response, and documents findings.

## SOC L1 workflow
1. Monitor alerts and queues.
2. Validate alert details and data quality.
3. Gather relevant host, user, time, IP, process, and threat-intelligence context.
4. Decide whether the alert is benign, suspicious, or likely an incident.
5. Follow playbooks, preserve evidence, escalate when required, and document actions.

## Terms
- **Event:** one recorded activity.
- **Alert:** a notification produced by a rule or analytic.
- **Incident:** a confirmed or sufficiently credible security case requiring coordinated handling.
- **False positive:** alert that does not represent the malicious condition it intended to detect.
- **IOC:** indicator associated with possible compromise, such as a domain, hash, or IP.
- **Telemetry:** security-relevant data from systems, identities, networks, and applications.

## Scenario
Several failed logins (Windows Event ID 4625) are followed by a successful login (4624). This sequence warrants review, but could also result from a user mistyping a password. Check account, source, timing, logon type, MFA/identity records, and activity after the success.

## Practice
Classify each as event, alert, or incident: a single failed login; a SIEM rule notifying analysts of 30 failures; validated evidence of unauthorized access requiring response. Explain why context matters.
