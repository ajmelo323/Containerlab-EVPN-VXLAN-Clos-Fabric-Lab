frr version 8.4_git
frr defaults traditional
hostname leaf2
no ipv6 forwarding
!
interface eth1
 ip address 10.0.2.1/31
exit
!
interface eth2
 ip address 10.0.2.3/31
exit
!
interface eth3
 ip address 192.168.2.1/24
exit
!
interface lo
 ip address 10.255.0.12/32
exit
!
router bgp 65102
 bgp router-id 10.255.0.12
 no bgp ebgp-requires-policy
 neighbor 10.0.2.0 remote-as 65000
 neighbor 10.0.2.2 remote-as 65000
 !
 address-family ipv4 unicast
  network 10.255.0.12/32
  network 192.168.2.0/24
 exit-address-family
 !
 address-family l2vpn evpn
  neighbor 10.0.2.0 activate
  neighbor 10.0.2.2 activate
  advertise-all-vni
  vni 100
   route-target import 100:100
   route-target export 100:100
  exit-vni
 exit-address-family
exit
!
