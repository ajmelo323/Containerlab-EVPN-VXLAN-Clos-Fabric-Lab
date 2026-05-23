frr version 8.4_git
frr defaults traditional
hostname leaf1
no ipv6 forwarding
!
interface eth1
 ip address 10.0.1.1/31
exit
!
interface eth2
 ip address 10.0.1.3/31
exit
!
interface eth3
 ip address 192.168.1.1/24
exit
!
interface lo
 ip address 10.255.0.11/32
exit
!
router bgp 65101
 bgp router-id 10.255.0.11
 no bgp ebgp-requires-policy
 neighbor 10.0.1.0 remote-as 65000
 neighbor 10.0.1.2 remote-as 65000
 !
 address-family ipv4 unicast
  network 10.255.0.11/32
 exit-address-family
 !
 address-family l2vpn evpn
  neighbor 10.0.1.0 activate
  neighbor 10.0.1.2 activate
  advertise-all-vni
  vni 100
   route-target import 100:100
   route-target export 100:100
  exit-vni
 exit-address-family
exit
!
