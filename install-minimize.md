# install minimize －》基本配置

１．ping www.baid.com  --&gt;  **unkonw ping www.baidu.com**

resolve:

```shell
  vi /etc/sysconfig/network-scripts/ifcfg-enoeno16777736
```

ifcfg-enoeno16777736 　enoeno16777736为自己网卡名称

##### 修改 ONBOOT=on 修改为ONBOOT=yes

保存后

service network start

ping www.baidu.com --&gt;ok

\(连接上网络\)

---

2.　把当前用户加入到sudo

```shell
su root  // 切换root 用户
vi /etc/sudoerss
```

在root ALL=\(ALL:ALL\) ALL　行下　把你想要用sudo 权限的用户加入　格式如下：

liuhua ALL=\(ALL:ALL\) ALL

---

3.静态ip 地址设置

```
如果使用静态ip地址，BOOTPROTO参数修改为static；
使用的dhcp方式获取动态ip，则改为的dhcp。如果禁止通过的dhcp   
获取到的dns配置覆盖手工配配置的dns服务器，则PEERDNS参数改为no。
ONBOOT参数修改为yes表示在系统启动时自动激活该网卡。
IPADDR设置ip地址，NETMASK设置子网掩码，GATEWAY设置网关。
最后使用：wq保存设置并退出。

IPV4_FAILURE_FATAL=no
IPADDR=192.168.3.70
NETMASK=255.255.255.0
GATEWAY=192.168.3.1
DNS1=114.114.114.114
```

```
vi编辑/etc/resolv.conf配置文件来配置dns域名解析服务器，添加运营商提供的dns服务器地址,这里是我的dns服务器配置，最后使用：wq保存并退出。

nameserver 202.96.199.133
nameserver 8.8.8.8
```

---

4.修改主机名

```
在CentOS或RHEL中，有三种定义的主机名:a、静态的（static），b、瞬态的（transient），以及 c、灵活的（pretty）。
“静态”主机名也称为内核主机名，是系统在启动时从/etc/hostname自动初始化的主机名。“瞬态”主机名是在系统运行时临时分配的主机名，例如，通过DHCP或mDNS服务器分配。静态主机名和瞬态主机名都遵从作为互联网域名同样的字符限制规则。而另一方面，“灵活”主机名则允许使用自由形式（包括特殊/空白字符）的主机名，
以展示给终端用户（如Dan's Computer）。

在CentOS/RHEL 7中，有个叫hostnamectl的命令行工具，它允许你查看或修改与主机名相关的配置。

要查看主机名相关的设置：

$ hostnamectl status

只查看静态、瞬态或灵活主机名，分别使用“--static”，“--transient”或“--pretty”选项。

$ hostnamectl status [--static|--transient|--pretty]

要同时修改所有三个主机名：静态、瞬态和灵活主机名：

$ sudo hostnamectl set-hostname <host-name>

就像上面展示的那样，在修改静态/瞬态主机名时，任何特殊字符或空白字符会被移除，而提供的参数中的任何大写字母会自动转化为小写。一旦修改了静态主机名，/etc/hostname 将被自动更新。然而，/etc/hosts 不会更新以保存所做的修改，所以你需要手动更新/etc/hosts。

如果你只想修改特定的主机名（静态，瞬态或灵活），你可以使用“--static”，“--transient”或“--pretty”选项。

例如，要永久修改主机名，你可以修改静态主机名：

$ sudo hostnamectl --static set-hostname <host-name>

注意，你不必重启机器以激活永久主机名修改。上面的命令会立即修改内核主机名。注销并重新登入后在命令行提示来观察新的静态主机名。
```

---

5.远程秘钥登录

```
ssh-keygen -t rsa  //生成秘钥　在用户目录.ssh 下pub 公钥
ssh root@192.168.60.110 "mkdir .ssh" 在远程root 目录下创建.ssh
rsync ~/.ssh/id_rsa.pub root@92.168.60.110:/root/.ssh/
ssh root@192.168.60.110 //登录远程服务器
cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys　//把公钥放在验证key值的文件中
// 可以远程登录　创建别名
vim vim ~/.zshrc
  alias sj70="ssh root@192.168.3.70"
  alias sj68="ssh root@192.168.3.68"
  alias sj69="ssh root@192.168.3.69"
//打开新pst 窗体　sj70
```

1. install on-my-zsh\(一种shell 的变种　操作方便\)

   ```shell
   yum install zsh

   sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
   ```

2. 查看ip 地址　网关

   ```shell
   ip addr //ip 地址
   ip route show // 网关
   ```

   3.rsync 远程同步失败

```shell
yum -y install openssh-clients
```

6.bash-shell 补全包

```shell
sudo yum install epel-release
yum install  bash-completion
yum install  bash-completion-extras
```



