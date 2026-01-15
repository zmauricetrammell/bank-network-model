# Control Placement – Lab 1

| Control | Location | Purpose |
|------|--------|--------|
| Guest isolation | Branch edge | Stop untrusted traffic at the source |
| Guest isolation | HQ WAN ingress | Defense-in-depth if branch control fails |
| Inter-branch blocking | HQ WAN ingress | Prevent lateral movement |
| Management access control | Branch edge | Restrict privileged access paths |
| Internet access control | HQ egress | Centralized audit and policy enforcement |

## Rationale
- Branch enforcement limits blast radius and WAN abuse.
- HQ enforcement ensures policy consistency and auditability.
- Multiple enforcement points reduce single-misconfiguration risk.
