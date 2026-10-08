# Windows Network Diagnostic Commands

A quick-reference sheet for the IT Support Lab.

## IP Configuration

```powershell
ipconfig
ipconfig /all
```

Use these to inspect interface addresses, subnet masks, gateways, DHCP status, and DNS servers.

## Connectivity

```powershell
ping 127.0.0.1
ping <LOCAL_IP>
ping <DEFAULT_GATEWAY>
ping 8.8.8.8
ping google.com
```

Test from the local TCP/IP stack outward.

## DNS

```powershell
nslookup google.com
ipconfig /displaydns
ipconfig /flushdns
```

Use `nslookup` to separate name-resolution problems from general connectivity problems.

## Routing

```powershell
tracert 8.8.8.8
route print
```

Use these to inspect the path traffic takes and the local routing table.

## ARP

```powershell
arp -a
```

Displays IPv4-to-MAC address mappings learned by the machine.

## PowerShell

```powershell
Get-NetIPConfiguration
Get-NetAdapter
Get-NetIPAddress
Get-DnsClientServerAddress
Test-NetConnection 8.8.8.8
Test-NetConnection google.com -Port 443
```

PowerShell provides structured Windows networking information and service-level connectivity tests.

## Rule

A command by itself is not troubleshooting.

Always record:

**Command → Result → Interpretation → Next action**
