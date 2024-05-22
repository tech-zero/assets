### Part 6 Commands (Net Management)
Set local clock to UTC on all devices.
#### Router ISP:
```
ntp master 3
end
```
#### Router EDGE
```
 ntp server 203.0.113.1
 logging trap warning
 logging host 172.16.100.5
 logging on
ip access-list standard SNMP-NMS
  permit host 172.16.100.5
  exit
 snmp-server contact Cisco ENCOR Student
 snmp-server community 31DAYS ro SNMP-NMS
 snmp-server host 172.16.100.5 version 2c 31DAYS
 snmp-server ifindex persist
 snmp-server enable traps bgp
 snmp-server enable traps config
 snmp-server enable traps ospf
end
```
#### Router HQ
```
 ntp server 172.16.10.1
 logging trap warning
 logging host 172.16.100.5
 logging on
ip access-list standard SNMP-NMS
  permit host 172.16.100.5
  exit
 snmp-server contact Cisco ENCOR Student
 snmp-server community 31DAYS ro SNMP-NMS
 snmp-server host 172.16.100.5 version 2c 31DAYS
 snmp-server ifindex persist
 snmp-server enable traps config
 snmp-server enable traps ospf
!
! The NetFlow configuration that follows will only work on IOS/IOSv devices.
!
ip flow-export version 9
ip flow-export destination 172.16.100.5 9999
interface g0/0/0
 ip flow ingress
 ip flow egress
!
!
end
```
#### Switch DIST1
```
 ntp server 172.16.10.1
 logging trap warning
 logging host 172.16.100.5
 logging on
ip access-list standard SNMP-NMS
  permit host 172.16.100.5
  exit
 snmp-server contact Cisco ENCOR Student
 snmp-server community 31DAYS ro SNMP-NMS
 snmp-server host 172.16.100.5 version 2c 31DAYS
 snmp-server ifindex persist
 snmp-server enable traps config
 snmp-server enable traps ospf
end
```
#### Switch DIST2
```
ntp server 172.16.10.1
 logging trap warning
 logging host 172.16.100.5
 logging on
ip access-list standard SNMP-NMS
  permit host 172.16.100.5
  exit
 snmp-server contact Cisco ENCOR Student
 snmp-server community 31DAYS ro SNMP-NMS
 snmp-server host 172.16.100.5 version 2c 31DAYS
 snmp-server enable traps config
 snmp-server enable traps ospf
end
```
#### Switch ASW1
```
 ntp server 172.16.10.1
 logging trap warning
 logging host 172.16.100.5
 logging on
ip access-list standard SNMP-NMS
  permit host 172.16.100.5
  exit
 snmp-server contact Cisco ENCOR Student
 snmp-server community 31DAYS ro SNMP-NMS
 snmp-server host 172.16.100.5 version 2c 31DAYS
 snmp-server ifindex persist
 snmp-server enable traps config
 snmp-server enable traps ospf
end
```
