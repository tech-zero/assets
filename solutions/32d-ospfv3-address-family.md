### OSPFv3 Address Families Configuration Lab Solution
```
R3
conf t
 router ospfv3 1
  router-id 3.3.3.3
   address-family ipv4
   address-family ipv6
  exit-address-family
!
interface GigabitEthernet 0/1
 ospfv3 1 ipv4 area 1
 ospfv3 1 ipv6 area 1
exit
!
interface GigabitEthernet 0/2
 ospfv3 1 ipv4 area 1
 ospfv3 1 ipv6 area 1
exit
!

R4
conf t
 router ospfv3 1
  router-id 4.4.4.4
   address-family ipv4
   address-family ipv6
  exit address-family
!
interface GigabitEthernet 0/1
 ospfv3 1 ipv4 area 1
 ospfv3 1 ipv6 area 1
exit
!
interface GigabitEthernet 0/2
 ospfv3 1 ipv4 area 0
 ospfv3 1 ipv6 area 0
exit
!

R5
conf t
 router ospfv3 1
  router-id 5.5.5.5
  address-family ipv4
   address-family ipv6
  exit address-family
!
interface GigabitEthernet 0/1
 ospfv3 1 ipv6 area 0
 ospfv3 1 ipv4 area 0
exit
!
interface GigabitEthernet 0/2
 ospfv3 1 ipv6 area 0
 ospfv3 1 ipv4 area 0
exit
!
end
```

#### Verification Commands
```
R4
show ospfv3 neighbor
show ospfv3 interface brief
show ospfv3 database
!
```

◀️ [Back to labs](https://github.com/tech-zero/ccnp-encor/blob/main/labs/32-ospf/4-ospfv3-address-family/README.md)
