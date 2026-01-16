# Security Intent – Lab 1

## Guest Network
- Guests are untrusted.
- Guests may access the internet only.
- Guests may not access:
  - Corporate HQ services
  - Branch user networks
  - Management networks
- Guests may use local network services required for connectivity
  (e.g., DHCP, DNS).

## User Network
- Users may access HQ services required for business operations.
- Users may access the internet through centralized HQ egress.
- Users may not access other branch LANs directly.

## Management Network
- Management access is privileged.
- Management devices may access:
  - Network infrastructure
  - HQ management services
- Management access is restricted from general internet use (optional,
  enforced later).

## Inter-Branch Policy
- Branch-to-branch lateral movement is denied by default.
- All inter-site communication must transit HQ.
