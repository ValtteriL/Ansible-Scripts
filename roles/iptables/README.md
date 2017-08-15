# Most basic iptables rules for VPS

Allow only incoming SSH
Allow all outgoing
Drop all forward

ipv4 & ipv6

```
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT ACCEPT
-A INPUT -s 127.0.0.0/8 -m comment --comment "Allow everything from localhost" -j ACCEPT
-A INPUT -m comment --comment "Allow established connections" -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -m comment --comment "Allow ssh from everywhere" -j ACCEPT
```

