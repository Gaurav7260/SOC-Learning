# Session 1 — Networking Foundations for SOC

## Objectives
Understand the network concepts that help an analyst interpret alerts and logs.

## Core notes
- **Network:** connected devices exchanging data.
- **IP address:** logical address used to route packets; private addresses are commonly used inside local networks.
- **MAC address:** link-layer interface identifier used on a local network.
- **Switch:** forwards frames within a LAN; **router:** forwards packets between networks.
- **Default gateway:** router address a host uses to reach other networks.
- **DNS:** translates names such as example.com into IP addresses.
- **TCP:** connection-oriented transport with delivery/order mechanisms. **UDP:** connectionless transport with less protocol overhead.
- **Port:** identifies an application/service endpoint on a host; examples include DNS 53, HTTP 80, HTTPS 443, SSH 22, RDP 3389.
- **OSI model:** Physical, Data Link, Network, Transport, Session, Presentation, Application. In investigations, think in terms of Ethernet/MAC, IP, TCP/UDP, and application protocols.

## SOC example
A workstation queries a newly observed domain. DNS telemetry helps show the requested name and returned answer; firewall or proxy telemetry helps determine whether a connection was attempted or allowed. Neither log alone proves malicious activity.

## Practice
1. Explain the difference between a MAC address and an IP address.
2. Why might DNS and firewall logs be correlated?
3. On macOS, inspect local interfaces with `ifconfig`; identify the active network interface without sharing public IPs or private details.
4. Explain what a default gateway does.

## Key takeaway
Network context makes endpoint and identity alerts more understandable. This is a foundation, not a claim that every event is suspicious.
