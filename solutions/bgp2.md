### BGP Lab 2 Solution
#### Configure BGP for IPv6 networks
#### R3
```
conf t
 route-map IPV6-NEXT-HOP
  set ipv6 next-hop 2000:2::1
exit
!
router bgp 65001
 neighbor 198.51.100.6 remote-as 65004
 address-family ipv4
  network 10.1.1.0 mask 255.255.255.0
  exit-address-family
 address-family ipv6
  network 2001:1::/64
  neighbor 198.51.100.6 activate
  neighbor 198.51.100.6 route-map IPV6-NEXT-HOP out
  exit-address-family
end
```
#### ISP
```
conf t
 route-map IPV6-NEXT-HOP
  set ipv6 next-hop 2000:2::2
exit
!
router bgp 65004
 neighbor 198.51.100.5 remote-as 65001
 address-family ipv4
  network 203.0.113.4 mask 255.255.255.252
  exit-address-family
 address-family ipv6
  network 2003:3::/64
  neighbor 198.51.100.5 activate
  neighbor 198.51.100.5 route-map IPV6-NEXT-HOP out
  exit-address-family
end
```
#### Verification Commands
#### ISP
```
show ip route
show ipv6 route
show bgp
show bgp ipv6 unicast
```
◀️ [Back to labs](https://github.com/tech-zero/ccnp-encor/blob/main/labs/3-infrastructure/_layer3/bgp/bgp2/README.md)
