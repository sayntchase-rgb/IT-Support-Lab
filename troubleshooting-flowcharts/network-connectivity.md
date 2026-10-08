# Network Connectivity Troubleshooting Flow

Use this sequence to isolate connectivity failures.

```text
START
  |
  v
Is the network adapter connected/enabled?
  |-- NO --> Fix physical/link/adapter problem
  |
 YES
  |
  v
Does the host have a valid IP configuration?
  |-- NO --> Investigate DHCP/static configuration
  |
 YES
  |
  v
Can 127.0.0.1 be reached?
  |-- NO --> Investigate local TCP/IP stack
  |
 YES
  |
  v
Can the local IP be reached?
  |-- NO --> Investigate adapter/IP configuration
  |
 YES
  |
  v
Can the default gateway be reached?
  |-- NO --> Investigate LAN/Wi-Fi/Ethernet/VLAN/gateway
  |
 YES
  |
  v
Can a public IP such as 8.8.8.8 be reached?
  |-- NO --> Investigate routing/WAN/upstream connectivity
  |
 YES
  |
  v
Can a domain name resolve?
  |-- NO --> Investigate DNS
  |
 YES
  |
  v
Can the required service/port be reached?
  |-- NO --> Investigate firewall/service/application
  |
 YES
  |
  v
Connectivity path is functioning
```

## Core Principle

Move from the **closest dependency to the farthest dependency**.

This prevents random troubleshooting and makes each test eliminate possible causes.
