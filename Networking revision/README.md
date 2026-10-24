# Networking Revision

A dedicated revision track for networking fundamentals used in SOC Analyst L1 investigations. This section is separate from the main SOC curriculum and Python learning.

## Revision approach

Each session uses:
1. Short theory notes
2. Practical examples
3. A real-world SOC scenario
4. Safe Mac-compatible exercises or clearly labelled simulated/public evidence
5. A quiz and weak-area review

## Progress

- [Session 01 — Networking Fundamentals](./01-networking-fundamentals.md)
  - Network basics, common ports, TCP/UDP, DNS and firewalls
  - Private/public IPv4, CIDR/subnet masks, default gateway and NAT
  - Mac Terminal diagnostic commands
  - Simulated firewall investigation and deny-event interpretation

## Safety and evidence notes

- Examples in this revision track are educational.
- The firewall records use documentation-only IP ranges (RFC 5737): `203.0.113.0/24`, `198.51.100.0/24`, and `192.0.2.0/24`.
- Do not treat a single allow/deny event as proof of compromise. Correlate with relevant logs and endpoint context.
- Review command output for private information before sharing it publicly.
