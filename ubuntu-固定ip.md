step 1:

```shell
➜  ~ sudo vim /etc/network/interfaces

auto enp4s0
iface enp4s0 inet static
address 172.20.10.210
gateway 172.20.10.1
netmask 255.255.255.0
dns-nameservers 114.114.114.114 8.8.8.8
```

setp 2: 

```shell
sudo ifdown enp4s0 && sudo ifup enp4s0

```



