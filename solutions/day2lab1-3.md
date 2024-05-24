### Day 2 Lab 1 Solution:
### Part 3 Commands (Routing Protocols)
#### Router EDGE
```router ospf 4
 router-id 0.0.4.1
 network 172.16.11.0 0.0.0.255 area 0
 network 172.16.13.0 0.0.0.255 area 0
 default-information originate
 exit
router ospfv3 6
 router-id 0.0.6.1
 address-family ipv6 unicast
  default-information originate
 exit
interface g0/0/1
 ospfv3 6 ipv6 area 0
 exit
interface g0/0/2
 ospfv3 6 ipv6 area 0
 exit
!
ip route 172.16.0.0 255.255.0.0 null0
ipv6 route 2001:db8:172::/48 null0
!
router bgp 65100
 bgp router-id 1.1.1.1
 neighbor 198.51.100.2 remote-as 65000
 neighbor 2001:db8:198:51::2 remote-as 65000
 address-family ipv4 unicast 
  neighbor 198.51.100.2 activate
  no neighbor 2001:db8:198:51::2 activate
  network 172.16.0.0 mask 255.255.0.0
  exit-address-family
 address-family ipv6 unicast
  no neighbor 198.51.100.2 activate
  neighbor 2001:db8:198:51::2 activate
  network 2001:db8:172::/48
  exit-address-family
```
#### Router ISP
```
ip route 0.0.0.0 0.0.0.0 loopback 0
ipv6 route ::/0 loopback 0
router bgp 65000
 bgp router-id 2.2.2.2
 neighbor 198.51.100.1 remote-as 65100
 neighbor 2001:db8:198:51::1 remote-as 65100
 address-family ipv4
  neighbor 198.51.100.1 activate
  no neighbor 2001:db8:198:51::1 activate
  network 203.0.113.1 mask 255.255.255.255
  network 0.0.0.0
  exit-address-family
 address-family ipv6
  no neighbor 198.51.100.1 activate
  neighbor 2001:db8:198:51::1 activate
  network 2001:db8:203:113::1/128
  network ::/0
  exit-address-family
```
#### Router HQ
```
router ospf 4
 router-id 0.0.4.2
 network 172.16.10.0 0.0.0.255 area 0
 network 172.16.13.0 0.0.0.255 area 0
 exit
router ospfv3 6
 router-id 0.0.6.2
 exit
interface g0/0/1
 ospfv3 6 ipv6 area 0
 exit
interface g0/0/2
 ospfv3 6 ipv6 area 0
 exit
end
```
#### Switch DIST1
```
router ospf 4
 router-id 0.0.4.3
 network 172.16.100.0 0.0.0.255 area 0
 network 172.16.101.0 0.0.0.255 area 0
 network 172.16.102.0 0.0.0.255 area 0
 network 172.16.11.0 0.0.0.255 area 0
 passive-interface default
 no passive-interface g1/0/11
 exit
router ospfv3 6
 router-id 0.0.6.3
 passive-interface default
 no passive-interface g1/0/11
 exit
interface g1/0/11
 ospfv3 6 ipv6 area 0
 exit
interface vlan 100
 ospfv3 6 ipv6 area 0
 exit
interface vlan 101
 ospfv3 6 ipv6 area 0
 exit
interface vlan 102
 ospfv3 6 ipv6 area 0
 exit
end
```
#### Switch DIST2
```
router ospf 4
 router-id 0.0.4.4
 network 172.16.100.0 0.0.0.255 area 0
 network 172.16.101.0 0.0.0.255 area 0
 network 172.16.102.0 0.0.0.255 area 0
 network 172.16.10.0 0.0.0.255 area 0
 passive-interface default
 no passive-interface g1/0/11
 exit
router ospfv3 6
 router-id 0.0.6.4
 passive-interface default
 no passive-interface g1/0/11
 exit
interface g1/0/11
 ospfv3 6 ipv6 area 0
 exit
interface vlan 100
 ospfv3 6 ipv6 area 0
 exit
interface vlan 101
 ospfv3 6 ipv6 area 0
 exit
interface vlan 102
 ospfv3 6 ipv6 area 0
 exit
end
```
◀️ [Back to lab](https://github.com/tech-zero/ccnp-encor/blob/main/labs/31dayrev/lab1/README.md)
