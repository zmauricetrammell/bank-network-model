# Lab 0 – NPB As-Is: HQ + 2 Branches (Centralized Egress)

## Purpose
Establish a minimal, realistic baseline model of a regulated hub-and-spoke network.

This lab proves:
- Branch-to-HQ connectivity across a simulated private WAN
- Centralized internet egress at HQ
- Basic segmentation and policy enforcement

No redundancy in Lab 0. Reliability comes later.

---

## Topology (Minimal)

Sites:
- HQ (Hub)
- Branch-1 (Spoke)
- Branch-2 (Spoke)
- WAN Cloud (Provider simulation)
- Internet Stub (simple external network)

Devices (suggested):
- HQ:
  - 1x Router (HQ-EDGE)
  - 1x Firewall (HQ-FW) [can be a router with ACLs if needed]
  - 1x L2 Switch (HQ-ACCESS) (optional if you want VLAN practice)
  - 1x Services host (DNS/AD/Logging stub)

- Each Branch:
  - 1x Router (BRx-EDGE)
  - 1x L2 Switch (BRx-ACCESS)
  - 2–3 end hosts (User PC, Guest client, Mgmt client)

WAN:
- 1x Router acting as “MPLS/Provider Cloud” interconnecting HQ and branches

Internet:
- 1x Router acting as “Internet”
- (Optional) 1x web server host to ping/curl

---

## VLAN / Segment Plan (Simplified)

Branch VLANs:
- VLAN 10: USERS
- VLAN 50: GUEST
- VLAN 99: MGMT

HQ segments:
- HQ-INSIDE: Corporate networks (branch traffic terminates here)
- HQ-SERVICES: DNS/AD/Logging stub
- HQ-OUTSIDE: Internet-facing

---

## Routing Assumptions
- Branches have a default route toward HQ over the WAN
- HQ knows branch networks (static routes for Lab 0)
- NAT occurs only at HQ (centralized egress)

---

## Security Policy (Lab 0)
- GUEST cannot reach USERS or MGMT
- USERS can reach HQ services (DNS stub)
- USERS can reach Internet via HQ (NAT)
- MGMT can reach network devices (management access)
- No inbound connectivity from Internet to inside networks

---

## Validation Checklist (What “Done” Means)

Connectivity:
- Branch USERS can ping HQ services
- Branch USERS can reach Internet (ping external router / web host)
- Branch GUEST can reach Internet
- Branch GUEST cannot reach Branch USERS or HQ services

Routing:
- Verify branch routing tables and HQ routes
- Confirm all internet traffic from branches egresses HQ

Security:
- Confirm blocked paths with explicit tests (ping/ssh fails)

Artifacts to capture:
- Screenshot of topology
- IP plan table
- Command outputs demonstrating:
  - routing
  - NAT
  - policy enforcement

---

## Stretch (Optional, only if time remains)
- Add VLAN 20 VOICE and VLAN 30 ATM segments (no need to fully implement services)
- Add syslog host and forward logs from routers/firewall

## Lab 0 – As-Is Network Validation

This lab models a Notional Pacific Bank current-state network with:

- Hub-and-spoke private WAN
- Centralized HQ services
- Centralized internet egress via HQ
- Static routing for clarity
- NAT performed only at HQ

### Verified Behaviors
- Branch users can reach HQ services
- HQ services can reach branch LANs
- Branch internet access is backhauled and NATed at HQ
- No direct branch-to-branch or branch-to-internet paths exist

This lab establishes a clean baseline before applying security controls,
segmentation, and automation in future labs.
