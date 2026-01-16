# ACL Logic – Lab # (NAME)

## Scope
- Location: Branch 1
- Source Zone: BR1-GUEST (10.1.50.0/24)
- Enforcement Point: Branch edge (inbound on guest LAN)

---

## Required Allows (in order)

1. Allow guest to reach local gateway
   - Reason: basic network connectivity

2. Allow guest DNS to corporate resolver
   - Source: 10.1.50.0/24
   - Destination: HQ-SVC (10.0.10.10)
   - Protocols: UDP/TCP 53
   - Reason: name resolution without exposing other services

3. Allow guest to reach the internet
   - Source: 10.1.50.0/24
   - Destination: Internet (203.0.113.0/24)
   - Reason: guest access requirement

---

## Explicit Denies

4. Deny guest to all corporate RFC1918 networks
   - Destination: 10.0.0.0/8
   - Reason: prevent access to HQ and other branches

5. Deny guest to WAN transport networks
   - Destination: 172.16.0.0/12
   - Reason: prevent probing internal transport

---

## Default Action

6. Permit remaining traffic
   - Reason: keep lab flexible; tighten later if needed

---

## Notes

- ICMP is not explicitly permitted to HQ services.
- Enforcement is duplicated at HQ in a later step (defense in depth).
