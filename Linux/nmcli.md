For modifying an old connection

```
nmcli connection modify <UUID or IFNAME> ipv4.method manual ipv4.addresses 192.168.64.61 ipv4.gateway 192.168.64.1 ipv4.dns 8.8.8.8,1.1.1.1
```

For down a connection
```
nmcli connection down <infname>
```
For up a connection
```
nmcli connection down <infname>
```
