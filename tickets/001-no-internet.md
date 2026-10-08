# Ticket 001 — Local Gateway Reachable, Internet Unreachable

**Status:** In progress  
**Category:** Networking / Connectivity  
**Platform:** Windows  
**Priority:** Normal  

## User Report

> The computer appears connected to the local network, but Internet resources cannot be reached.

## Objective

Determine why the workstation can communicate with the local gateway but cannot reach the public Internet.

Do not assume DNS is the cause. Test the network layer-by-layer.

## Environment

Baseline captured with `ipconfig /all` before making configuration changes.

- Hostname: Redacted from public portfolio
- Windows version: Not yet recorded
- Active network adapter: Realtek Wi-Fi 6 adapter
- IPv4 address: `192.168.1.241`
- Subnet mask: `255.255.255.0` (`/24`)
- Default gateway: `192.168.1.254`
- DHCP: Enabled
- DHCP server: `192.168.1.254`
- DNS servers: `8.8.8.8`, `8.8.4.4` and an ISP-provided IPv6 resolver
- Connection type: Wi-Fi
- Additional adapter observed: VirtualBox host-only adapter at `192.168.56.1/24` with no default gateway

> Public-facing documentation intentionally omits physical MAC addresses and global IPv6 addresses because they are unnecessary for demonstrating the troubleshooting process.

## Initial Symptoms

Record exactly what works and what fails.

- [x] Network adapter is connected
- [x] Valid IPv4 address is assigned
- [x] Default gateway is present
- [x] Gateway responds to ping
- [ ] Public IP responds to ping
- [ ] Domain name resolves
- [ ] Website loads

## Investigation

### 1. Inspect IP Configuration

```powershell
ipconfig /all
```

Observed baseline:

```text
Active interface: Wi-Fi
IPv4: 192.168.1.241
Subnet: 255.255.255.0 (/24)
Gateway: 192.168.1.254
DHCP Enabled: Yes
DHCP Server: 192.168.1.254
DNS: 8.8.8.8, 8.8.4.4, ISP IPv6 resolver
```

Interpretation:

The workstation has a valid private IPv4 address on the `192.168.1.0/24` network, DHCP is active, and a default gateway is configured. The active Internet-facing interface is Wi-Fi. A separate VirtualBox host-only interface exists but has no default gateway, so it is not being treated as the primary Internet path.

### 2. Test the Local TCP/IP Stack

```powershell
ping 127.0.0.1
```

Result:

```text
4 packets sent, 4 received, 0 lost (0% loss)
Round-trip time: <1 ms
TTL: 128
```

Interpretation:

The loopback test succeeded with no packet loss. This confirms that the local Windows TCP/IP stack is functioning correctly. The failure, if present, is farther outward than the local protocol stack.

### 3. Test the Local Interface

```powershell
ping 192.168.1.241
```

Result:

```text
4 packets sent, 4 received, 0 lost (0% loss)
Round-trip time: <1 ms
TTL: 128
```

Interpretation:

The workstation successfully responded on its assigned Wi-Fi IPv4 address. This confirms that the local interface and IPv4 configuration are responding correctly. The next step is to test communication with the default gateway.

### 4. Test the Default Gateway

```powershell
ping 192.168.1.254
```

Result:

```text
4 packets sent, 4 received, 0 lost (0% loss)
Minimum: 1 ms
Maximum: 5 ms
Average: 2 ms
TTL: 64
```

Interpretation:

The default gateway responded successfully with no packet loss. This confirms that the workstation can communicate across the local Wi-Fi network to the router. The local path from the PC to the gateway is functioning, so the next test moves beyond the LAN to a public Internet IP address.

### 5. Test Internet Reachability Without DNS

```powershell
ping 8.8.8.8
```

Result:

```text
PENDING
```

### 6. Test DNS Resolution

```powershell
nslookup google.com
```

Result:

```text
PENDING
```

### 7. Trace the Route

```powershell
tracert 8.8.8.8
```

Result:

```text
PENDING
```

### 8. Inspect ARP Information

```powershell
arp -a
```

Relevant observations:

```text
PENDING
```

## Troubleshooting Logic

Interpret the results instead of guessing:

| Test | Success Means | Failure Suggests |
|---|---|---|
| `ping 127.0.0.1` | TCP/IP stack is functioning | Local TCP/IP problem |
| Ping local IP | Adapter/IP stack responds | Adapter/configuration issue |
| Ping gateway | Local LAN path works | LAN, Wi-Fi/Ethernet, VLAN, or gateway issue |
| Ping `8.8.8.8` | Internet routing works | WAN/routing/upstream issue |
| `nslookup google.com` | DNS works | DNS configuration/server issue |
| `tracert 8.8.8.8` | Shows route progression | Helps locate where traffic stops |

## Hypothesis

Write the hypothesis **after** gathering evidence.

```text
PENDING
```

## Root Cause

Do not complete this section until the lab proves the cause.

```text
PENDING
```

## Resolution

Document the exact change made.

```text
PENDING
```

## Verification

Repeat the relevant tests after remediation.

```powershell
ping 192.168.1.254
ping 8.8.8.8
nslookup google.com
```

Final result:

```text
PENDING
```

## Evidence

Add screenshots to `/screenshots/` and reference them here.

Example:

```markdown
![Gateway ping](../screenshots/001-gateway-ping.png)
```

## Lessons Learned

```text
PENDING
```

## Interview Explanation

After completing the lab, summarize the case in 3–5 sentences:

- What failed?
- How did you isolate it?
- What evidence identified the root cause?
- What did you change?
- How did you verify the fix?
