step 1:

```shell
➜  ~ sudo vim /etc/network/interfaces

auto enp0s3
iface enp0s3 inet static
address 192.168.9.147
netmask 255.255.255.0
gateway 192.168.9.1
dns-nameservers 192.168.1.32 58.240.57.33
dns-domain ad.vipmro.com
#dns-search ad.vipmro.com
```

setp 2:

```shell
sudo ip addr flush enp0s3
sudo systemctl restart networking.service
```



