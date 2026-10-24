# Session 4 — Security Data Sources

## Common sources and their value
- **Windows Security logs:** logon, account, privilege, and audit activity.
- **Linux logs:** authentication, system, service, and privilege-use activity; exact locations vary by distribution.
- **Firewall:** allowed/blocked connection metadata, source/destination, ports, and rule.
- **DNS:** requested domain, response, and resolver context.
- **Proxy/web gateway:** web requests, URL/category, user, and policy action.
- **EDR:** endpoint process, file, registry, network, and behavioural detections.
- **Email security:** sender, recipient, authentication results, URLs/attachments, and delivery action.
- **Identity/cloud audit:** sign-ins, MFA, role changes, and administrative actions.

## Scenario: suspicious email
Email telemetry may show a spoofed sender or suspicious attachment. Endpoint telemetry may show a document spawning PowerShell; DNS/firewall logs may show a related connection. Correlate timestamps and entities before making a conclusion.

## Review
1. Authentication logs record logon-related events; EDR alerts flag suspicious endpoint behaviour.
2. DNS shows queried names/responses; firewall telemetry helps establish whether related traffic was attempted, allowed, or blocked.
3. Correlation connects events across sources by time, user, device, IP, process, or domain.
4. Suspicious behaviour is not proof: legitimate administration and unusual-but-benign activity can resemble attacks.

## Practice
For a suspicious email, list which fields you would seek from email, endpoint, identity, and network sources. Do not open suspicious attachments or visit live malicious links.
