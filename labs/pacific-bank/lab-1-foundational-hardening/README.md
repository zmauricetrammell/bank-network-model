# Lab 1 – Security & Segmentation Hardening

## Purpose
Apply defense-in-depth controls to the Lab 0 network without changing
its routing topology or breaking availability.

This lab focuses on **policy enforcement**, not new connectivity.

## In Scope
- Guest isolation
- Inter-branch lateral movement prevention
- Privileged management access
- Defense-in-depth (branch + HQ)

## Out of Scope
- SD-WAN
- VRFs everywhere
- Automation
- Vendor-specific firewall features
- Cloud security controls

## Design Constraints
- Lab 0 routing and NAT must remain functional
- Changes must be incremental and reversible
- Controls must be auditable and explainable
