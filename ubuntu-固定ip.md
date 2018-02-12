step 1:

```shell
➜  ~ sudo vim /etc/network/interfaces

auto enp4s0
iface enp4s0 inet static
address 172.20.10.210
gateway 172.20.10.1
netmask 255.255.255.0
nameserver 8.8.8.8
```

setp 2: 

```shell
sudo ip addr flush enp4s0
```

step 3:重启 networking 服务

```shell
sudo systemctl restart networking.service
```

setp 4: 配置DNS

```shell
➜  ~ sudo vim /etc/resolvconf/resolv.conf.d/base 

nameserver 8.8.8.8

➜  ~ sudo resolvconf -u  #读取dns 配置
```



