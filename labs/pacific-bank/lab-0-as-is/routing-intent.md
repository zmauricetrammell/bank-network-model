# Lab 0 Routing Intent

## Branch behavior (BR1-RTR / BR2-RTR)
- Default route points to WAN-RTR (toward HQ)
- No direct route to Internet
- No direct route to other branch LANs (inter-site transits HQ)

## WAN behavior (WAN-RTR)
- Routes between branches and HQ (static for Lab 0)
- No NAT
- No security policy enforcement (transport only)

## HQ behavior (HQ-RTR)
- Has routes back to branch LANs (static for Lab 0)
- Performs NAT for all inside networks toward INET-RTR
- Acts as centralized egress (matches current-state assumptions)

## Internet behavior (INET-RTR)
- Acts as “the internet”
- Provides reachability to 203.0.113.0/24
- No routes back to inside networks beyond the HQ link
