### Day 2 Lab 1 Solution:
#### Part 2 Commands
#### Switch DIST1
```
interface range g2/0-3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 12 mode active
 exit
interface range g1/0-1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 1 mode active
 exit
spanning-tree mode rapid-pvst
spanning-tree vlan 100,102 root primary
spanning-tree vlan 101 root secondary
interface g0/0
 switchport mode access
 switchport access vlan 100
 spanning-tree portfast
 exit
end
```
#### Switch DIST2
```
interface range g2/0-3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 12 mode active
 exit
interface range g1/2-3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 2 mode active
 exit
!
spanning-tree mode rapid-pvst
spanning-tree vlan 101 root primary
spanning-tree vlan 100,102 root secondary
!
interface g0/0
 switchport mode access
 switchport access vlan 102
 spanning-tree portfast
 exit
end
```
#### Switch ASW1
```
spanning-tree mode rapid-pvst
interface range g1/0-1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 1 mode active
 exit
interface range g1/2-3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 999
 channel-group 2 mode active
 exit
interface g3/2
 switchport mode access
 switchport access vlan 100
 spanning-tree portfast
 exit
interface g3/3
 switchport mode access
 switchport access vlan 101
 spanning-tree portfast
 exit
end
```
◀️ [Back to lab](https://github.com/tech-zero/ccnp-encor/blob/main/labs/31dayrev/lab1/README.md)
