### Socat

```
 socat tcp-listen:80,fork,reuseaddr,forever tcp-connect:13.251.60.115:80
 socat tcp-listen:5353,fork,reuseaddr,forever udp-connect:localhost:53
```
