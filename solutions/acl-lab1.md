### Named Extended ACLs Lab
#### R1 (ACL for PC1)
```
conf t
ip access-list extended TELNET_ONLY
 permit tcp 10.1.1.10 0.0.0.255 host 10.1.3.10 eq 23
 permit icmp 10.1.1.10 0.0.0.255 host 10.1.3.10
exit
!
interface GigabitEthernet 0/2
 ip access-group TELNET_ONLY in
 exit
end
```
#### Verification Commands from PC1
```
ping 10.1.3.10 (!!!!!) Should succeed because of the ACL
ping 10.1.2.10 (.....) Should fail because of the new ACL
telnet 10.1.3.10 80 (Should be blocked)
telnet 10.1.3.10
(Trying 10.1.3.10 ...Open) should be successful
```
#### R1 (ACL for PC2)
```
conf t
ip access-list extended HTTP_ONLY
 permit tcp 10.1.2.10 0.0.0.255 host 10.1.3.10 eq www
 permit icmp 10.1.1.10 0.0.0.255 host 10.1.3.10
exit
!
interface GigabitEthernet 0/3
 ip access-group HTTP_ONLY in
 exit
end
```
#### Verification Commands from PC2
```
ping 10.1.3.10 (!!!!!) Ping server should succeed because of the ACL
ping 10.1.1.10 (.U.U.U) Pings to PC1 should fail because of the new ACL
telnet 10.1.3.10 80 (Should be blocked)
telnet 10.1.3.10 80
(Trying 10.1.3.10 ...Open) Telnet should be successful
```
◀️ [Back to lab](https://github.com/tech-zero/ccnp-encor/blob/main/labs/ACLs/lab1/README.md)
