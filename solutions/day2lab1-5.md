### Part 5 Commands (Security)
#### All Devices:
```
enable algorithm-type SCRYPT secret 31daysENCOR
username admin privilege 15 algorithm-type SCRYPT secret 31daysENCOR
```
#### All devices except R2:
```
aaa new-model
radius server RADIUS
 address ipv4 172.16.100.6 auth-port 1812 acct-port 1813
 key 31daysRADIUS
 exit
aaa authentication login default group radius local
end
```
◀️ [Back to lab](https://github.com/tech-zero/ccnp-encor/blob/main/labs/31dayrev/lab1/README.md)
