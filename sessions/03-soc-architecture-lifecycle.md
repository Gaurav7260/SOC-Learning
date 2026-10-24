# Session 3 — SOC Architecture and Monitoring Lifecycle

## Typical flow
Data sources → collection/forwarding → SIEM or analytics platform → detection logic → alert queue → investigation and triage → response/escalation → lessons learned and tuning.

## Data sources
Endpoints, Windows/Linux logs, identity providers, firewalls, DNS/proxy, email security, cloud audit trails, and threat intelligence.

## Detection logic
Rules identify patterns, thresholds, known indicators, or correlations. Example: 30 failed logins from one source in 60 seconds may trigger an alert. Thresholds should reflect environment and baseline behaviour; one rule does not establish compromise.

## Correlation
Join records using shared attributes such as timestamp, username, hostname, source IP, process, domain, or event identifier. Normalize time zones and account for clock skew.

## Simulated exercise
Given 30 failed logins in one minute followed by one successful login:
- Identify the detection condition.
- List three contextual checks.
- State what evidence would support escalation.
- Name at least two benign explanations.

## Analyst note
Distinguish raw events from rule-generated alerts and confirmed incidents. Detection quality depends on both coverage and tuning.
