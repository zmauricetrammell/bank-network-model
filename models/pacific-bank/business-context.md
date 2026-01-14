# Business Context – Notional Pacific Bank

This model is based on a hypothetical but realistic interpretation of
:contentReference[oaicite:0]{index=0}
as a regulated financial institution operating across multiple geographic regions.

The intent is to practice enterprise infrastructure design, security segmentation,
and operational decision-making under regulatory constraints.

---

## Organizational Overview

- Regional bank operating across:
  - Hawaiʻi
  - Guam
  - Saipan
- Approximately 50 branch locations
- Single primary corporate headquarters located in Honolulu
- Centralized IT organization (no branch-level IT staff)

Branches are treated as operational edge sites, not autonomous environments.

---

## Operating Model Assumptions

- Core IT services are centralized at headquarters or controlled data centers
- Branches connect to HQ via a private WAN (e.g., MPLS or equivalent)
- Most user and application traffic is backhauled to HQ for inspection and control
- Limited or no local decision-making at branches

This reflects a risk-averse, audit-focused operating model common in banking.

---

## Regulatory and Security Context

The organization is assumed to operate under:
- FDIC regulatory oversight
- NIST-aligned security frameworks
- Routine internal and external audits

Security priorities include:
- Strong internal segmentation
- Least-privilege access enforcement
- Centralized logging and monitoring
- Controlled internet egress
- Formal change management processes

---

## Technology Posture (High-Level)

- Centralized identity (e.g., Active Directory)
- Hybrid cloud usage for selected services (e.g., email, collaboration)
- On-prem or tightly controlled environments for core banking systems
- Enterprise wireless at branches and HQ
- Segmented networks for:
  - Users
  - Voice
  - ATMs
  - CCTV / physical security
  - Guest access
  - Management

All technology choices favor control, consistency, and auditability over flexibility.

---

## Modeling Philosophy

This model does not attempt to replicate any proprietary or confidential architecture.

Instead, it focuses on:
- Translating business and regulatory requirements into network design
- Evaluating trust boundaries and traffic flows
- Creating a foundation suitable for automation and infrastructure-as-code
- Practicing safe, repeatable changes with minimal operational risk
