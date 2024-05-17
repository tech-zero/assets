### OSPFv3 Traditional Configuration Lab Solution

```
R3
config t
ipv6 unicast-routing
ipv6 cef
!
ipv6 router ospf 1
 router-id 3.3.3.3
exit
!
interface GigabitEthernet 0/1
 ipv6 ospf 1 area 1
exit
!
interface GigabitEthernet 0/2
 ipv6 ospf 1 area 1
exit
!

R4
conf t
 ipv6 unicast-routing
 ipv6 cef
!
ipv6 router ospf 1
 router-id 4.4.4.4
exit
!
interface GigabitEthernet 0/1
 ipv6 ospf 1 area 1
exit
!
interface GigabitEthernet 0/2
 ipv6 ospf 1 area 0
exit
!

R5
conf t
 ipv6 unicast-routing
 ipv6 cef
!
ipv6 router ospf 1
 router-id 5.5.5.5
 passive-interface lo0
exit
!
interface GigabitEthernet 0/1
 ipv6 ospf 1 area 0
exit
!
interface GigabitEthernet 0/2
 ipv6 ospf 1 area 0
exit
!

```

#### Verification Commands

```
R3
show ipv6 ospf inteface brief
show ipv6 ospf neighbor
show ipv6 ospf database
!
Check out the OSPF link state database
- Type 1 LSA
- Type 2 LSA
- Type 3 LSA (InterArea IA prefix link states)

```

◀️ [Back to labs](https://github.com/tech-zero/ccnp-encor/blob/main/labs/32-ospf/3-ospfv3-traditional/README.md)
