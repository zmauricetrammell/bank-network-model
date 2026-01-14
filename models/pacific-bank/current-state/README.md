# Current-State Network – Notional Pacific Bank (As-Is)

This document describes the assumed current-state ("as-is") network architecture
used as the baseline for lab simulations.

The goal is to model a plausible, stable enterprise banking network prior to
any modernization or optimization efforts.

---

## High-Level Architecture

- Hub-and-spoke WAN topology
- Corporate headquarters acts as the primary hub
- Branch locations act as spoke sites
- Centralized internet egress at HQ
- Centralized security enforcement

Branches are treated as untrusted or semi-trusted edge environments.

---

## Headquarters (HQ)

HQ is assumed to host or terminate:

- WAN aggregation for all branches
- Central firewalls
- Internet egress
- Core routing and switching
- Data center or data center interconnect
- Centralized services such as:
  - Identity (e.g., Active Directory)
  - DNS / DHCP
  - Logging / SIEM
  - Management and monitoring platforms

HQ is considered the primary trust anchor for the enterprise network.

---

## Branch Locations

Each branch is assumed to contain:

- One integrated edge device (router/firewall)
- One or more access switches
- Enterprise wireless access points
- An IT closet with standardized hardware

Typical branch network segments include:
- User workstations (tellers, office staff)
- Voice (IP phones)
- ATMs
- CCTV / physical security systems
- Guest Wi-Fi
- Network management

Branches do not host core services and rely on HQ for authentication, logging,
and policy enforcement.

---

## Traffic Flow Assumptions

- User and application traffic is backhauled to HQ
- Internet access is mediated by centralized firewalls and proxy controls
- Inter-branch traffic traverses HQ
- Guest Wi-Fi may be locally isolated but is not trusted

---

## Security Posture (As-Is)

- Strong network segmentation
- Least-privilege access enforced through identity and network controls
- No direct access between sensitive segments (e.g., ATMs, CCTV, users)
- Centralized logging and monitoring
- Formal change management processes

The current-state prioritizes stability, control, and auditability over agility.

---

## Known Constraints

- Legacy WAN technologies may still be in use
- Limited flexibility at branch sites
- Changes require coordination and approval
- Automation may exist but is not assumed to be pervasive

These constraints are intentional and will inform future-state improvements.
