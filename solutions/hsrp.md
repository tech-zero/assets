### HSRP Lab Solution

#### Lab Tasks:
 - Configure HSRP for servicing the virtual IP address 10.1.1.1
 - R1 = Active Router, R2 = Standby Router
 - Configure routers to reclaim roles in case of a failure
 - Test failover configuration

```
R1
!
config t
interface gi0/2
 standby 10 ip 10.1.1.1
 standby 10 priority 110
 standby 10 preempt
end
!

R2 
!
config t
interface gi0/2
 standby 10 ip 10.1.1.1
 standby 10 preempt
end
!
```

Verification from PC
```
traceroute 1.1.1.1
!
ping 1.1.1.1 repeat 99999
!

R1
config t
interface gi0/2
 shutdown
!

PC
Verify the standby IP address failed over
!

R1
config t
interface gi0/2
 no shutdown
!

PC
Verify the standby IP address is reclaimed by R1
and the traceroute points to R1's ip address.
!
```
:white_check_mark: [CLI reference](https://github.com/tech-zero/assets/blob/main/solutions/bgp2.md)
