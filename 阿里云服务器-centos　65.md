# 服务器设置

1. df -lh  \(文件系统磁盘使用　只有５０G,一共３00\)

   ![](/assets/Screenshot from 2016-11-12 23-21-19.png)
2. fdisk -l  \(查看所有磁盘\)　　  

   ![](/assets/Screenshot from 2016-11-12 23-26-11.png)  
   　\/dev\/sdb 未挂载使用下面开始分区，格式化设置文件系统并自动挂载

   **如果自动挂载的硬盘被取出应该先把自动挂载设置去掉　不然京能进入救援模式　注释配置**

   3.fdisk /dev/sdb \(分区\)
     
   ![](/assets/Screenshot from 2016-11-12 23-37-59.png)  
   4.设置swap 分区  
   
   ![](/assets/Screenshot from 2016-11-12 23-40-14.png)  
       键入　w 回车保存修改  
       分区已经完成了\(还有空间没分配，我准备之后做测试使用，你可以全部分配\)  
   ５． mkfs.ext3 \/dev\/sdb1\(设置文件系统\)  
   
   ![](/assets/Screenshot from 2016-11-12 23-45-14.png)  
   6.设置swap 并挂载　（swapon swapoff）  
   
   ![](/assets/Screenshot from 2016-11-12 23-49-45.png)  
   7.挂载　\/dev\/sdb1 并设置开机启动默认挂载 \/dev\/sdb1 和　\/dev\/sdb2\(swap\)  
   
   ![](/assets/Screenshot from 2016-11-12 23-55-21.png)

   \`\`\`  
   vi /etc/fstab                 //添加下面内容在末尾　\(如果移除硬盘要先把配置注销\)  
   /dev/sdb1 /mnt ext3 defaults 0 0　  
   /dev/sdb2 nono swap defaults 0 0   
   :wq  
   mount -a //Mount all filesystems \(of the given types\) mentioned in fstab　测试挂载硬盘，在重启之前操作，防止无法启动机器

   ---

   ## 挂载硬盘结束　下面时服务器软件安装 mysql mongdb tomcat

   ### 1.[install mysql 5.7](http://dev.mysql.com/doc/refman/5.7/en/linux-installation-yum-repo.html)


### 修改mysql 默认存储路径\(centos 6.5 mysql 5.7\)

1. Stop MySql
   ```
   service mysqld stop
   ```

2. Change Data Directory

```
cp -rap /var/lib/mysql /data/mysql  chown mysql.mysql /data/mysql
```

Now edit MySQL default configuration file /etc/my.cnf and update values of datadir   
and socket variable.

```
Change From:
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
Change To:   
datadir=/data/mysql
socket=/data/mysql/mysql.sock
:wq
service mysqld start

## iptables 配置
```

modprobe ip\_tables  //阿里云iptables 无法启动　执行添加依赖  
modprobe iptable\_filter

lsmod \|grep iptable

service iptables start  
//转发80 端口数据到 8080\(tomcat 配置的端口\)  
iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080

\`\`\`
