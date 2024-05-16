### OSPFv2 Lab Solution
```
!
R3
conf t
 router ospf 1
  network 0.0.0.0 255.255.255.255 area 1
 exit
!
R4
conf t
 router ospf 1
  network 4.4.4.4 0.0.0.0 area 1
  network 0.0.0.0 198.51.100.0 0.0.0.3 area 1
  network 0.0.0.0 203.0.113.0 0.0.0.3 area 0
 exit
!
R5
conf t
 router ospf 1
  network 0.0.0.0 255.255.255.255 area 0
 exit
!
```

### Verification Commands
```
!
R5
show ip route
show ip ospf database
!

R4
show ip ospf database
!
end
!
Because R4 is an ABR, you'll notice
the output is much larger since R4
has interfaces in both area 0 & area 1.
```

◀️ [Back to labs](https://github.com/tech-zero/ccnp-encor/blob/main/labs/32a-ospfv2.md)
