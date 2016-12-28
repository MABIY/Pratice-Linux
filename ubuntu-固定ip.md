```shell
sudo gedit /etc/network/interfaces
```
表示使用gedit编辑器打开interfaces文件。 在打开的文件中，若有内容，先全部删除。然后输入如下代码：  
```shell
auto loiface lo inet loopback
auto ens33iface ens33 inet staticaddress 
192.168.8.100netmask 255.255.255.0
gateway 192.168.8.2
```
然后，配置DNS服务器：
在里面填入阿里的DNS：223.5.5.5
nameserver 223.5.5.5

sudo /etc/init.d/networking restart
