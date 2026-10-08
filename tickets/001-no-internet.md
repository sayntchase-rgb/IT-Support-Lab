# Ticket 001 — Local Gateway Reachable, Internet Unreachable

**Status:** Ready to run  
**Category:** Networking / Connectivity  
**Platform:** Windows  
**Priority:** Normal  

## User Report

> The computer appears connected to the local network, but Internet resources cannot be reached.

## Objective

Determine why the workstation can communicate with the local gateway but cannot reach the public Internet.

Do not assume DNS is the cause. Test the network layer-by-layer.

## Environment

Fill these in during the lab.

- Hostname:
- Windows version:
- Network adapter:
- IPv4 address:
- Subnet mask/prefix:
- Default gateway:
- DNS server(s):
- Connection type: Wi-Fi / Ethernet

## Initial Symptoms

Record exactly what works and what fails.

- [ ] Network adapter is connected
- [ ] Valid IPv4 address is assigned
- [ ] Default gateway is present
- [ ] Gateway responds to ping
- [ ] Public IP responds to ping
- [ ] Domain name resolves
- [ ] Website loads

## Investigation

### 1. Inspect IP Configuration

```powershell
ipconfig /all
```

Record:

```text
IPv4:
Subnet:
Gateway:
DNS:
DHCP Enabled:
```

### 2. Test the Local TCP/IP Stack

```powershell
ping 127.0.0.1
```

Result:

```text
PENDING
```

### 3. Test the Local Interface

Replace `<LOCAL_IP>` with the workstation address.

```powershell
ping <LOCAL_IP>
```

Result:

```text
PENDING
```

### 4. Test the Default Gateway

Replace `<GATEWAY_IP>` with the actual gateway.

```powershell
ping <GATEWAY_IP>
```

Result:

```text
PENDING
```

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
ping <GATEWAY_IP>
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
