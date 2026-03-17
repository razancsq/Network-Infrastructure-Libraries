# Network Infrastructure for Eastern Province Public Libraries

**Course:** CIS 315 - Communication and Network Fundamentals  
**University:** Imam Abdulrahman Bin Faisal University  
**Tool:** Cisco Packet Tracer

---

## Project Overview

A full network infrastructure design connecting two public library branches in the Eastern Province of Saudi Arabia. The project focuses on building a secure, scalable, and reliable network with seamless inter-library communication.

---

## Network Architecture

```
                    ┌─────────────────────────────────────┐
                    │         Serial Link (RIP)            │
                    │                                      │
          ┌─────────┴──────┐                    ┌──────────┴─────┐
          │    ISP-R1      │                    │    ISP-R2      │
          └─────────┬──────┘                    └──────────┬─────┘
                    │                                      │
               ┌────┴────┐                           ┌────┴────┐
               │   R1    │                           │   R2    │
               │(Gateway)│                           │(Gateway)│
               └────┬────┘                           └────┬────┘
                    │                                      │
            ┌───────┴────────┐                   ┌────────┴───────┐
            │  Switch0       │                   │   Switch7      │
            │  (Core)        │                   │   (Core)       │
            └──┬─────┬───┬───┘                   └──┬──────┬───┬──┘
               │     │   │                          │      │   │
           Sw1  Sw2  Sw3  NTP-Server            Sw4  Sw5  Sw6  NTP-Server
            │    │    │                           │    │    │
          PCs  PCs  PCs                         PCs  PCs  PCs
         Phones Phones Phones                 Phones Phones Phones

        |────────── Library A ──────────|  |────────── Library B ──────────|
```

### Each Branch Includes
- PCs (PC0–PC8) connected via access switches
- IP Phones with Voice VLAN
- NTP Server connected to core switch for time synchronization
- Hierarchical design: Core switch → Access switches → End devices

---

## Technologies Used

| Technology | Purpose |
|-----------|---------|
| VLANs | Traffic segmentation (Data & Voice) |
| RIP Routing | Dynamic route sharing between libraries |
| DHCP | Automatic IP assignment for PCs and IP Phones |
| NTP | Time synchronization across all devices |
| Option 150 | Telephony configuration for IP Phones |

---

## Security Features

- Traffic segmentation using VLANs
- DHCP exclusion for critical IP ranges
- Access Control Lists (ACLs)
- Firewall and encryption protocols

---

## IP Addressing

| Segment | Subnet |
|---------|--------|
| Library A - Data VLAN | 192.168.10.160/27 |
| Library A - Voice VLAN | 192.168.10.192/27 |
| Library B - Data VLAN | 192.168.10.32/27 |
| Library B - Voice VLAN | 192.168.10.64/27 |
| Inter-router Link | 192.168.10.128/27 |

---

## Testing Results

Connectivity tested via ping between all PCs across both libraries.

| Test | Result |
|------|--------|
| PC0 to Library B | Success |
| PC1 to Gateway | Success (0% loss) |
| PC2 to ISP Link | Success (0% loss) |
| PC4 to Cross-library | Success (0% loss) |
| PC5 to Remote Gateway | Success (0% loss) |

---

## Files

| File | Description |
|------|-------------|
| `Final_library.pkt` | Cisco Packet Tracer simulation file |

---

## How to Open

1. Install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
2. Open `Final_library.pkt`
3. Explore the topology and test connectivity using the simulation mode

---

## Author

**Razan Alqahtani**  
Computer Science Student — IAU
