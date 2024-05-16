### OSPF Route Filtering Lab Solution
Initial checks: 

From R5, verify that you see the two inter-area routes being learned from area 1 192.0.20. and 198.51.100.0.

```
R5
!
show ip route

R4
!
config t
 ip prefix-list NO-AREA1-NETS seq 10 deny 192.0.2.0/30
 ip prefix-list NO-AREA1-NETS seq 20 deny 198.51.100.0/30
 ip prefix-list NO-AREA1-NETS seq 30 permit 0.0.0.0/0 le 32
!
router ospfv3 1
 address-family ipv4 unicast
  area 0 filter-list prefix NO-AREA1-NETS in
end
!

```

#### Verification Commands
Final check:

From R5, verify that the two inter-area routes, from before are now being filtered with the installed prefix-list

```
R5
show ip route
!
```

◀️ [Back to labs](https://github.com/tech-zero/ccnp-encor/blob/main/labs/32-ospf/2-route-filter/README.md)
