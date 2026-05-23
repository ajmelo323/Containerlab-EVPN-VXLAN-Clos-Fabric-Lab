# EVPN/VXLAN Clos Fabric Lab using Containerlab + FRRouting

## Overview

This project demonstrates a Linux-based Clos fabric built with **Containerlab** and **FRRouting (FRR)** inside an Ubuntu virtual machine.

The lab was created to strengthen understanding of modern data center networking concepts used in cloud, hyperscale, AI infrastructure, and network-as-a-service environments.

This is a **phone-safe flat repository layout**. All files are intentionally placed at the root level so GitHub mobile upload does not scramble folders or rename files incorrectly.

## Topology

- 2 Spine Nodes
- 3 Leaf Nodes
- 3 Linux Hosts
- Multi-AS eBGP underlay
- EVPN overlay configuration on leaf VTEPs
- VNI 100 with route-target import/export policies

## ASN Design

| Node | Role | ASN |
|---|---|---|
| spine1 | Spine | 65000 |
| spine2 | Spine | 65000 |
| leaf1 | Leaf/VTEP | 65101 |
| leaf2 | Leaf/VTEP | 65102 |
| leaf3 | Leaf/VTEP | 65103 |

## Technologies Used

- Containerlab
- Docker
- FRRouting
- Ubuntu Linux
- BGP
- EVPN
- VXLAN concepts
- Linux networking
- YAML topology automation

## File Layout

```text
README.md
clos-lab.yml
spine1-frr.conf
spine1-daemons
spine2-frr.conf
spine2-daemons
leaf1-frr.conf
leaf1-daemons
leaf2-frr.conf
leaf2-daemons
leaf3-frr.conf
leaf3-daemons
bgp-summary.png
evpn-config.png
topology-diagram.md
lab-status.md
validation-commands.md
linkedin-project-description.md
bgp-summary-output.md
```

## Underlay Architecture

The underlay uses **eBGP** between the spines and leaves.

The spines operate in ASN 65000 while each leaf operates in its own ASN. This simulates a routed Clos design where point-to-point links provide scalable transport between leaf and spine nodes.

Validated underlay elements:

- Spine-to-leaf BGP neighbor establishment
- Separate ASNs per leaf
- /31 routed point-to-point interfaces
- Loopback advertisement into BGP
- BGP route exchange across the Clos fabric

## EVPN Overlay Configuration

EVPN is configured under the `l2vpn evpn` address-family.

The VNI-specific EVPN configuration is placed on the **leaf nodes**, because the leaves represent the VTEP role in this lab design.

Configured EVPN elements:

- `address-family l2vpn evpn`
- EVPN neighbor activation
- `advertise-all-vni`
- `vni 100`
- Route-target import `100:100`
- Route-target export `100:100`

## Deployment

```bash
sudo containerlab deploy -t clos-lab.yml
```

## Validation

```bash
sudo docker exec -it clab-clos-lab-spine1 vtysh
show bgp summary
show bgp l2vpn evpn
```

## Current Lab Status

### Working

- Containerlab topology deployment
- FRRouting container startup
- Spine/leaf interface creation after redeploy
- eBGP underlay establishment
- Multi-AS Clos fabric design
- Loopback route advertisement
- EVPN address-family configuration
- VNI 100 route-target policy configuration on leaves

### Future Improvements

- Full VXLAN dataplane implementation
- Linux bridge/VXLAN interface integration
- MAC/IP advertisement validation
- End-to-end host reachability across VNI 100
- Add BFD sessions for fast failure detection
- Add ECMP failover testing
- Add automation using Ansible or Nornir

## Author

**Anwar Deen**

Network Engineer focused on modern data center networking, EVPN/VXLAN, Linux networking, automation, and hyperscale infrastructure.
