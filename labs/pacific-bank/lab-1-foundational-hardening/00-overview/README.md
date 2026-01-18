# Lab 1 – Security & Segmentation Hardening

## Purpose
Apply defense-in-depth controls to the Lab 0 network without changing
its routing topology or breaking availability.

This lab focuses on **policy enforcement**, not new connectivity; incrementally hardening the network by addressing guest access, lateral branch movement, management access, and centralized enforcement, in that order.

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

## Architecture Reference

This lab implements controls defined in:
- models/notional-pacific-bank/current-state/diagrams/logical/npb-lab1-security-overlay.drawio
