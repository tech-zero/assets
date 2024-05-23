### Day 2 Lab 1 Solution:
#### Part 2 Commands
#### Switch DIST1
```
interface range g2/0-3
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 12 mode active
 no shutdown
 exit
interface range g1/0-1
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 1 mode active
 no shutdown
 exit
spanning-tree mode rapid-pvst
spanning-tree vlan 100,102 root primary
spanning-tree vlan 101 root secondary
interface g0/0
 switchport mode access
 switchport access vlan 100
 spanning-tree portfast
 no shutdown
 exit
end
```
#### Switch DIST2
```
interface range g2/0-3
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 12 mode active
 no shutdown
 exit
interface range g1/2-3
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 2 mode active
 no shutdown
 exit
!
spanning-tree mode rapid-pvst
spanning-tree vlan 101 root primary
spanning-tree vlan 100,102 root secondary
!
interface g1/0/23
 switchport mode access
 switchport access vlan 102
 spanning-tree portfast
 no shutdown
 exit
end
```
#### Switch ASW1
```
spanning-tree mode rapid-pvst
interface range g1/0-1
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 1 mode active
 no shutdown
 exit
interface range g1/2-3
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 2 mode active
 no shutdown
 exit
interface g3/2
 switchport mode access
 switchport access vlan 100
 spanning-tree portfast
 no shutdown
 exit
interface g3/3
 switchport mode access
 switchport access vlan 101
 spanning-tree portfast
 no shutdown
 exit
end
```
◀️ [Back to lab](https://github.com/tech-zero/ccnp-encor/blob/main/labs/_ciscopress/lab1/README.md)
