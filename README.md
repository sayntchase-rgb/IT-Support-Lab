# IT Support Lab

A hands-on portfolio project documenting realistic IT support and troubleshooting scenarios using a structured help-desk workflow.

## Purpose

This repository demonstrates practical skills in:

- Windows troubleshooting
- TCP/IP networking
- DNS and DHCP diagnostics
- Command-line troubleshooting
- Root-cause analysis
- Technical documentation
- Verification and escalation
- Help-desk ticket writing

## Lab Method

Each troubleshooting case follows the same process:

1. Identify the reported problem.
2. Record symptoms without assuming the cause.
3. Establish the scope of the problem.
4. Gather system and network information.
5. Form and test a hypothesis.
6. Apply the least disruptive fix.
7. Verify normal operation.
8. Document the root cause, resolution, and lessons learned.

## Repository Structure

```text
IT-Support-Lab/
├── README.md
├── tickets/
│   ├── 001-no-internet.md
│   └── TICKET_TEMPLATE.md
├── screenshots/
│   └── .gitkeep
├── commands/
│   └── windows-network-diagnostics.md
├── troubleshooting-flowcharts/
│   └── network-connectivity.md
└── lessons-learned.md
```

## Ticket Progress

| Ticket | Scenario | Status |
|---|---|---|
| 001 | Computer can reach local gateway but cannot reach the Internet | Ready to run |

## Ticket #001

The first lab investigates a Windows computer that can communicate with its local gateway but cannot reach the public Internet.

The investigation uses tools such as:

- `ipconfig /all`
- `ping`
- `nslookup`
- `tracert`
- `arp -a`
- PowerShell network commands

See [`tickets/001-no-internet.md`](tickets/001-no-internet.md).

## Portfolio Standard

Every completed ticket should contain:

- Problem statement
- Environment
- Symptoms
- Scope
- Commands used
- Evidence
- Hypothesis
- Root cause
- Resolution
- Verification
- Lessons learned

Screenshots should support the investigation, not replace written explanation.

## Planned Cases

Future cases will include:

- DNS resolution failure
- DHCP configuration failure
- Incorrect default gateway
- IP address conflict
- Slow workstation
- High CPU or memory usage
- Windows service failure
- User permissions problem
- SSH connection failure
- Disk space incident

## Skills Demonstrated

**IT Support:** troubleshooting methodology, ticket documentation, verification  
**Networking:** IPv4, gateways, DNS, DHCP, ICMP, routing  
**Windows:** command-line diagnostics and system configuration  
**Security mindset:** evidence gathering, least-change remediation, documentation

---

This repository is part of an entry-level IT and cybersecurity portfolio.
