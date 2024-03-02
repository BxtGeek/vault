For CentOS, network configuration is typically done using the NetworkManager service. To set a static IP, create or edit the appropriate configuration file in /etc/sysconfig/network-scripts/. For example, for interface eth0, create or edit /etc/sysconfig/network-scripts/ifcfg-eth0:
```
TYPE=Ethernet
BOOTPROTO=none
DEFROUTE=yes
NAME=eth0
DEVICE=eth0
ONBOOT=yes
IPADDR=10.10.10.213
PREFIX=24
GATEWAY=10.10.10.1
DNS1=10.10.10.1
```

Then, restart the network service:
```
sudo systemctl restart network
```
