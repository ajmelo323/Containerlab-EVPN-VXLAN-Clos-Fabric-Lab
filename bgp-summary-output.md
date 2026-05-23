# BGP Summary Output

```text
spine1# show bgp summary

IPv4 Unicast Summary (VRF default):
BGP router identifier 10.255.0.101, local AS number 65000 vrf-id 0
BGP table version 9
RIB entries 9, using 1728 bytes of memory
Peers 3, using 2151 KiB of memory

Neighbor        V         AS   MsgRcvd   MsgSent   TblVer  InQ OutQ  Up/Down State/PfxRcd   PfxSnt Desc
10.0.1.1        4      65101        14        15        0    0    0 00:06:09            1        5 N/A
10.0.2.1        4      65102        14        15        0    0    0 00:06:07            2        5 N/A
10.0.3.1        4      65103        13        13        0    0    0 00:05:06            1        5 N/A

Total number of neighbors 3

L2VPN EVPN Summary (VRF default):
BGP router identifier 10.255.0.101, local AS number 65000 vrf-id 0
BGP table version 0
RIB entries 0, using 0 bytes of memory
Peers 3, using 2151 KiB of memory

Neighbor        V         AS   MsgRcvd   MsgSent   TblVer  InQ OutQ  Up/Down State/PfxRcd   PfxSnt Desc
10.0.1.1        4      65101        14        15        0    0    0 00:06:09            0        0 N/A
10.0.2.1        4      65102        14        15        0    0    0 00:06:07            0        0 N/A
10.0.3.1        4      65103        13        13        0    0    0 00:05:06            0        0 N/A

Total number of neighbors 3
```
