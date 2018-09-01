### Socat

```
 socat tcp-listen:80,fork,reuseaddr,forever tcp-connect:13.251.60.115:80
 socat tcp-listen:5353,fork,reuseaddr,forever udp-connect:localhost:53
```


### Iptable

```
iptables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination <Team-IP-ADDRESS>:80
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -I FORWARD -j ACCEPT
iptables -P FORWARD ACCEPT
sysctl net.ipv4.ip_forward=1

```
