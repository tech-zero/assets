### VRF Lab Solution
```
COMMON 
- Configure ip vrf statements
- Configure virtual interfaces
- Configure VRF routing with OSPF
!
config t
 ip vrf TENANT-A
 ip vrf TENANT-B
 ip vrf TENANT-C
exit
!
interface GigabitEthernet 0/1
 no shutdown
exit
!
interface GigabitEthernet 0/1.2
 encapsulation dot1q 2
  ip vrf forwarding TENANT-A
  ip address 192.0.2.1 255.255.255.252
exit
!
interface GigabitEthernet 0/1.3
 encapsulation dot1q 3
 ip vrf forwarding TENANT-B
 ip address 198.5.1.100.1 255.255.255.252
exit
!
interface GigabitEthernet 0/1.4
 encapsulation dot1q 4
 ip vrf forwarding TENANT-C
 ip address 203.0.113.1 255.255.255.252
exit
!
router ospf 1 vrf TENANT-A
 network 0.0.0.0 255.255.255.255 area 0
exit
!
!
router ospf 2 vrf TENANT-B
 network 0.0.0.0 255.255.255.255 area 0
exit
!
router ospf 3 vrf TENANT-A
 network 0.0.0.0 255.255.255.255 area 0
end

```

#### Verification Commands
```
COMMON
!
show ip route vrf TENANT-A
show ip route vrf TENANT-B
show ip route vrf TENANT-C
!
```

◀️ [Back to labs](https://github.com/tech-zero/ccnp-encor/blob/main/labs/_vir/lab1/README.md)
