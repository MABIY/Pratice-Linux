

step 1: 

```shell
➜  ~ sudo vim /etc/NetworkManager/NetworkManager.conf

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true  ＃修改
```

step 2:

```shell
➜  ~ sudo vim /etc/network/interfaces

auto enp4s0
iface enp4s0 inet static
address 172.20.10.210
gateway 172.20.10.1
netmask 255.255.255.0
nameserver 8.8.8.8
```

step 3:重启 networking 服务

```shell
sudo systemctl restart networking.service
```

setp 4: 配置DNS

```shell
➜  ~ sudo vim /etc/resolvconf/resolv.conf.d/base 

nameserver 223.5.5.5

➜  ~ sudo resolvconf -u  #读取dns 配置
```



