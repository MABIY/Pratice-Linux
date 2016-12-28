# ubunut 16.04 为root 设置　密码并修改ssh配置　可以root 远程登陆．

1. sudo passwd ＞输入当前密码　＞输入root 密码　＞　本地可以root 登陆（ssh root not work）
2. sudo apt install ssh
3. 修改配置文件　 \/etc\/ssh\/sshd\_config＞注释掉　PermitRootLogin prohibit-password　＞在下一行添加PermitRootLogin yes　＞service ssh restart（重启ssh service ）

---

### Linux下创建的用户is not in the sudoers file解决方法

1.sudo vi \/etc\/sudoers \(remove  \/etc\/sudoers.tmp\)

2.style:  
    root    ALL=\(ALL:ALL\) ALL  
    liuhua  ALL=\(ALL:ALL\) ALL

```
save then can sudo start.
```

---

### 压缩文件

tar.xz

```shell
压缩 tar.xz：

tar Jcvf file_name.tar.xz dir_name

centos:可与安装xz工具
yum install -y xz
解压缩 tar.xz：

tar Jxvf file_name.tar.xz

--strip-components 舍弃第一层文件夹
tar -zxvf ~/jdk-8.tar.gz -C . --strip-components 1
```

curl 使用　socks5　代理

```shell
--socks5-hostname localhost:9050 
curl --socks5-hostname localhost:9050 ftp://ftp.vim.org/pub/vim/unix/vim-7.3.tar.bz2 -O vim7.3.bz2
```

---

# 清理内核

```
To list all kernel:
dpkg --get-selections | grep "linux-image-[[:digit:]].*" | tr "\t" ";" | cut -d ";" -f1

The results looks somewhat like this:

linux-image-3.19.0-7-generic
linux-image-3.18.0-13-generic
linux-image-3.16.0-23-generic

Don't delete all kernels, only old ones!

Next let's remove the 3.16 kernel,
sudo apt-get purge linux-image-3.16.0-23-generic

and then all unused packages from the system:
sudo apt-get autoclean && sudo apt-get autoremove
```



