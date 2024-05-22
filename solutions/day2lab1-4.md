### Part 4 Commands (FHRP/SLA)
#### Switch DIST1
```
ip sla 4
 icmp-echo 172.16.11.1
 frequency 5
 exit
ip sla 6
 icmp-echo 2001:db8:172:11::1
 frequency 5
 exit
ip sla schedule 4 life forever start-time now
ip sla schedule 6 life-forever start-time now
track 4 ip sla 4
 delay down 10 up 15
 exit
track 6 ip sla 6
 delay down 10 up 15
 exit
interface vlan 100
 standby version 2
 standby 104 ip 172.16.100.254
 standby 104 priority 150
 standby 104 preempt
 standby 104 track 4 decrement 60
 standby 106 ipv6 autoconfig
 standby 106 priority 150
 standby 106 preempt
 standby 106 track 6 decrement 60
 exit
interface vlan 101
 standby version 2
 standby 114 ip 172.16.101.254
 standby 114 preempt
 standby 114 track 4 decrement 60
 standby 116 ipv6 autoconfig
 standby 116 preempt
 standby 116 track 6 decrement 60
 exit
interface vlan 102
 standby version 2
 standby 124 ip 172.16.102.254
 standby 124 priority 150
 standby 124 preempt
 standby 124 track 4 decrement 60
 standby 126 ipv6 autoconfig
 standby 126 priority 150
 standby 126 preempt
 standby 126 track 6 decrement 60
 exit
end
```
#### Switch DIST2
```
ip sla 4
 icmp-echo 172.16.10.1
 frequency
exit
ip sla 6
 icmp-echo 2001:db8:172:10::1
 frequency
exit
ip sla schedule 4 life forever start-time now
ip sla schedule 6 life forever start-time now
track 4 ip sla 4
 delay down 10 up 15
 exit
track 6 ip sla 6
 delay down 10 up 15
 exit
interface vlan 100
 standby version 2
 standby 104 ip 172.16.100.254
 standby 104 preempt
 standby 104 track 4 decrement 60
 standby 106 ipv6 autoconfig
 standby 106 preempt
 standby 106 track 6 decrement 60
 exit
interface vlan 101
 standby version 2
 standby 114 ip 172.16.101.254
 standby 114 priority 150
 standby 114 preempt
 standby 114 track 4 decrement 60
 standby 116 ipv6 autoconfig
 standby 116 priority 150
 standby 116 preempt
 standby 116 track 6 decrement 60
 exit
interface vlan 102
 standby version 2
 standby 124 ip 172.16.102.254
 standby 124 preempt
 standby 124 track 4 decrement 60
 standby 126 ipv6 autoconfig
 standby 126 preempt
 standby 126 track 6 decrement 60
 exit
end
```
◀️ [Back to lab](https://github.com/tech-zero/ccnp-encor/blob/main/labs/_ciscopress/lab1/README.md)
