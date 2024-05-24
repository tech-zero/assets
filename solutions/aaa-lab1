### AAA Lab Solution
#### R1
```
conf t
 aaa new-model
 username test secret cisco
 tacacs server TACACS1 
  address ipv4 10.1.1.10
  key security
 exit
!
 tacacs server TACACS2
  address ipv4 10.1.1.20
  key security
 exit
!
aaa group server tacacs+ T-GROUP
 server name TACACS1
 server name TACACS2
exit
!
 aaa authentication login default group T-GROUP local enable
!
 aaa authorization exec default group T-GROUP local
exit
!
logout
```
#### Verification Login with the credentials 

◀️ [Back to main](https://github.com/tech-zero/ccnp-encor/blob/main/labs/aaa/lab1/README.md)
