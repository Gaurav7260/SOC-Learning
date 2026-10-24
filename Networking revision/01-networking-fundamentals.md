# Session 01 — Networking Fundamentals Revision

**Track:** Networking Revision  
**Audience:** SOC Analyst L1 preparation  
**Environment:** macOS Terminal  
**Status:** In progress

## Learning objectives

By the end of this revision session, be able to:
- Explain what a network is and why networking knowledge matters in a SOC.
- Recognize common ports and distinguish TCP from UDP.
- Explain DNS and firewall allow/deny events.
- Distinguish private IPv4 addresses from public addresses.
- Read a basic CIDR prefix and explain a default gateway.
- Explain how NAT affects attribution in network logs.
- Use basic macOS commands to inspect local network configuration.

## 1. Networking basics

A computer network is a group of connected devices that communicate using agreed protocols. In a SOC, network telemetry helps analysts investigate scanning, suspicious outbound connections, command-and-control traffic, lateral movement and possible data exfiltration.

### Core concepts

- **IP address:** Identifies an interface at the IP layer; used to interpret source and destination fields.
- **Port:** Identifies a transport-layer endpoint associated with an application service.
- **TCP:** Connection-oriented transport that provides reliable, ordered delivery.
- **UDP:** Datagram-based transport without TCP-style delivery guarantees.
- **DNS:** Resolves names and provides other DNS records; suspicious query patterns can support an investigation.
- **Firewall:** Applies configured rules to network traffic. An allow/deny action is not, by itself, a verdict about malicious intent.

### Common ports

| Port | Common service | SOC context |
|---:|---|---|
| 21 | FTP | Legacy file transfer; check whether it is expected |
| 22 | SSH | Remote administration and login attempts |
| 25 | SMTP | Mail transfer |
| 53 | DNS | Domain lookups; inspect unusual domains and query patterns |
| 80 | HTTP | Unencrypted web traffic |
| 443 | HTTPS | Encrypted web traffic; the port alone does not prove the application is safe |
| 445 | SMB | Windows file sharing; useful in lateral-movement investigations |
| 3389 | RDP | Remote desktop access; unexpected exposure may warrant review |

These are conventional port assignments, not guarantees that a service is running on that port.

## 2. Private IPv4 vs public IPv4

The following IPv4 ranges are reserved for private networks:

| Private range | Typical context |
|---|---|
| `10.0.0.0/8` | Large private or corporate networks |
| `172.16.0.0/12` | Private networks |
| `192.168.0.0/16` | Home and small-office networks |

Private addresses are normally not routed directly over the public internet. A public IPv4 address is globally routable in ordinary circumstances, subject to routing and policy.

**Important:** A private address is not automatically trustworthy, and a public address is not automatically malicious.

## 3. Subnet masks and CIDR

A subnet mask or CIDR prefix identifies the network portion of an IPv4 address.

Example:
- Host address: `192.168.1.25`
- Example subnet: `192.168.1.0/24`
- Equivalent mask: `255.255.255.0`

A `/24` prefix means 24 of the 32 IPv4 bits are in the network prefix. This subnet has 256 total addresses; in a conventional IPv4 LAN subnet, 254 are typically usable host addresses.

**SOC relevance:** Subnet information helps analysts identify network segments, assess whether hosts are on the same subnet, and interpret internal scanning or traffic between segments.

## 4. Default gateway

A default gateway is the router or routing device a host uses as the next hop for destinations not covered by a more specific route.

Example:
```text
Laptop:          192.168.1.25
Default gateway: 192.168.1.1
Destination:     An external server
```

A gateway's firewall, routing or NAT logs may help correlate internal devices with outbound activity.

## 5. NAT — Network Address Translation

NAT modifies address information as traffic passes through a network device. Home and office routers commonly use source NAT, often with port translation, so multiple private IPv4 hosts can share one public IPv4 address for outbound connections.

**SOC relevance:** If many internal systems share a public IP, an analyst may need NAT translation records and timestamps (and sometimes port details) to attribute a connection to an internal host.

## 6. macOS practical exercises

Run these locally in Terminal. Interface names vary; Wi-Fi is often `en0`, but verify your active interface first.

### A. Identify hardware ports
```bash
networksetup -listallhardwareports
```

### B. Check the IPv4 address (replace en0 if needed)
```bash
ipconfig getifaddr en0
```

### C. Inspect the default route
```bash
route -n get default
```
Look for the gateway and interface fields.

### D. Inspect IPv4 routes
```bash
netstat -rn -f inet
```

### E. Inspect DNS resolver configuration
```bash
scutil --dns
```
macOS can show multiple resolvers; this alone is not suspicious.

### F. Resolve a domain
```bash
nslookup example.com
```

### G. Test basic reachability
```bash
ping -c 4 example.com
```
No ping reply does not prove a host is down; ICMP may be filtered.

### H. Check HTTPS response headers
```bash
curl -I https://example.com
```
Results may vary. Review command output before sharing it; it can contain local network details.

## 7. Simulated SOC scenario: outbound connections

**All events below are fictional.** The IP ranges shown are reserved for documentation, not real destinations.

| Time (UTC) | Source IP | Destination IP | Destination port | Protocol | Action |
|---|---|---|---:|---|---|
| 10:00:01 | 192.168.1.25 | 203.0.113.20 | 443 | TCP | Allowed |
| 10:00:03 | 192.168.1.26 | 203.0.113.20 | 443 | TCP | Allowed |
| 10:00:05 | 192.168.1.25 | 198.51.100.40 | 22 | TCP | Denied |

### Initial observations

- Two internal hosts connected to the same documentation-only destination on port 443.
- One host attempted an SSH-associated connection on port 22, and the firewall denied it.
- These records alone do not prove either benign or malicious activity.

### Sensible next steps

1. Confirm the assets, owners, timestamps and expected network behavior.
2. Check DNS, proxy and related firewall events.
3. Review repetition, destination context and any successful connections.
4. Correlate endpoint process telemetry and authentication logs.
5. Document evidence, uncertainty and the reason for any escalation.

### Why a deny event does not prove compromise

A firewall deny event means the connection was blocked according to the firewall's rules. It does not explain why the attempt occurred. Possible explanations include:
- Legitimate software attempting a connection disallowed by policy.
- A misconfigured application or incorrect destination.
- An unauthorized or suspicious connection attempt.

A SOC analyst should investigate context and correlate evidence before concluding that the endpoint is compromised.

**Interview takeaway:** A deny action proves that the firewall blocked the connection; it does not prove that the source device is compromised.

## 8. Knowledge check

1. Which is a private IPv4 address?
   - A. `8.8.8.8`
   - B. `192.168.1.25`
   - C. `1.1.1.1`

2. What does `/24` mean?
   - A. 24 host devices exactly
   - B. 24 network-prefix bits
   - C. 24 open ports

3. What is a default gateway commonly used for?
   - A. Forwarding traffic toward other networks
   - B. Resolving every domain name
   - C. Encrypting every packet

4. Why may NAT logs matter to an investigation?
   - A. They can help map translated traffic back to an internal host
   - B. They prove all HTTPS traffic is safe
   - C. They replace endpoint logs

5. A firewall blocks an outbound SSH connection. What can you conclude from that event alone?
   - A. The endpoint is definitely compromised
   - B. The firewall blocked the connection
   - C. The destination is definitely malicious

### Answer key

1. B — `192.168.0.0/16` is private.
2. B — CIDR `/24` specifies a 24-bit network prefix.
3. A — a default gateway provides a next hop for off-subnet destinations.
4. A — NAT records can help correlate translated traffic to an internal host.
5. B — a deny action is not a verdict on endpoint compromise.

## Revision checklist

- [ ] Revise private/public IPv4 ranges.
- [ ] Explain CIDR `/24` without notes.
- [ ] Identify the default gateway on the Mac.
- [ ] Explain why NAT can complicate attribution.
- [ ] Explain why a firewall deny event does not prove compromise.
- [ ] Complete the Terminal exercises and quiz.

## Next topic

Continue networking revision with the OSI and TCP/IP models, encapsulation, MAC addresses, ARP, switches and routers. This revision track remains separate from the main SOC curriculum and Python learning.
