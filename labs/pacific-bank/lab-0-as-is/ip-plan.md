# Lab 0 IP Plan – FHB As-Is (HQ + 2 Branches)

## Naming
- HQ Router: HQ-RTR
- Branch routers: BR1-RTR, BR2-RTR
- WAN provider router: WAN-RTR
- Internet router: INET-RTR

## Site Subnets (Inside)
HQ:
- HQ-SVC (services stub): 10.0.10.0/24  (GW: 10.0.10.1 on HQ-RTR)

Branch 1:
- BR1-USERS: 10.1.10.0/24 (GW: 10.1.10.1 on BR1-RTR)
- BR1-GUEST: 10.1.50.0/24 (GW: 10.1.50.1 on BR1-RTR)
- BR1-MGMT:  10.1.99.0/24 (GW: 10.1.99.1 on BR1-RTR)

Branch 2:
- BR2-USERS: 10.2.10.0/24 (GW: 10.2.10.1 on BR2-RTR)
- BR2-GUEST: 10.2.50.0/24 (GW: 10.2.50.1 on BR2-RTR)
- BR2-MGMT:  10.2.99.0/24 (GW: 10.2.99.1 on BR2-RTR)

## WAN Point-to-Point Links (/30)
HQ-RTR <-> WAN-RTR:   172.16.0.0/30
- HQ-RTR:  172.16.0.1
- WAN-RTR: 172.16.0.2

BR1-RTR <-> WAN-RTR:  172.16.0.4/30
- BR1-RTR: 172.16.0.5
- WAN-RTR: 172.16.0.6

BR2-RTR <-> WAN-RTR:  172.16.0.8/30
- BR2-RTR: 172.16.0.9
- WAN-RTR: 172.16.0.10

## HQ to Internet
HQ-RTR <-> INET-RTR:  198.51.100.0/30
- HQ-RTR:   198.51.100.1
- INET-RTR: 198.51.100.2

Internet “external” network: 203.0.113.0/24
- INET-RTR: 203.0.113.1
- Optional web server: 203.0.113.10
