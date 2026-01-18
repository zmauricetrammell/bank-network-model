# ACL Logic – Lab 1.1 (Zone Isolation)

## Scope 1.1a
- Location: Branch 1
- Source Zone: BR1-GUEST (10.1.50.0/24)
- Enforcement Point: Branch edge (inbound on guest LAN)

---

## Required Allows (in order)

1. Allow guest to reach local gateway
   - Reason: basic network connectivity

2. Allow guest DNS to corporate resolver
   - Source: 10.1.50.0/24
   - Destination: HQ-SVC (10.0.10.100)
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

## Scope 1.1b
- Location: Branch 1
- Source Zone: BR1-USER (10.1.10.0/24)
- Enforcement Point: Branch edge (inbound on USER LAN)

---

## Required Allows (in order)

1. Allow user to reach local gateway
   - Reason: basic network connectivity

2. Allow user to corporate servers
   - Source: 10.1.10.0/24
   - Destination: HQ-SVC (10.0.10.100)
   - Reason: allow HQ services to users

3. Allow users to reach the internet
   - Source: 10.1.10.0/24
   - Destination: Internet (203.0.113.0/24)
   - Reason: allow users to cloud services and internet

---

## Explicit Denies

4. Deny users to all corporate RFC1918 networks
   - Destination: 10.0.0.0/8
   - Reason: prevent access to other Users, Guests, Management, and other branches

5. Deny users to WAN transport networks
   - Destination: 172.16.0.0/12
   - Reason: prevent probing internal transport and isolate compromised systems

---

## Default Action

6. Permit remaining traffic
   - Reason: keep lab flexible; tighten later if needed

---

## Notes

- ICMP is not explicitly permitted to HQ services.
- Enforcement is duplicated at HQ in a later step (defense in depth).

## Scope 1.1c
- Location: Branch 1
- Source Zone: BR1-MANAGEMENT (10.1.99.0/24)
- Enforcement Point: Branch edge (inbound on management LAN)

---

## Required Allows (in order)

1. Allow management to reach local gateway
   - Reason: basic network connectivity

2. Allow management to corporate servers
   - Source: 10.1.99.0/24
   - Destination: HQ-SVC (10.0.10.100)
   - Reason: allow HQ services to managment

3. Allow management to branch networks
   - Destination: 10.1.0.0/16
   - Reason: allow access to other Users, Guests, Management within branch
---

## Explicit Denies

4. Deny management to reach the internet
   - Source: 10.1.99.0/24
   - Destination: Internet (203.0.113.0/24)
   - Reason: blocked for general internet


5. Deny users to WAN transport networks
   - Destination: 172.16.0.0/12
   - Reason: prevent probing internal transport and isolate compromised systems

---

## Default Action

6. Permit remaining traffic
   - Reason: keep lab flexible; tighten later if needed

---

## Notes

- ICMP is not explicitly permitted to HQ services.
- Enforcement is duplicated at HQ in a later step (defense in depth).