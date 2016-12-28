# centos 6.5服务器配置
##mongodb  
  安装 根据官网步骤。
  ```sh
  locate mongo //查看系统mongo 装在哪里
  
  /var/lib/mongodb/   文件锁定目录 删除重启
  ```
  
  [参考网址](http://www.cnblogs.com/alexqdh/archive/2011/11/25/2263626.html)
  
1. mongodb 3.2 安装好后 修改/etc/mongod.cnf 文件 binip 注释掉 或改为本地ip地址（非 127.0.0.1）
   远程可连接。

##mysql 
Your root account, and this statement applies to any account, may only have been added with localhost access (which is recommended).  

You can check this with:
```sh
SELECT host FROM mysql.user WHERE User = 'root';  
```
If you only see results with localhost and 127.0.0.1, you cannot connect from an external source. If you see other IP addresses, but not the one you're connecting from - that's also an indication.

You will need to add the IP address of each system that you want to grant access to, and then grant privileges:
```sh
CREATE USER 'root'@'ip_address' IDENTIFIED BY 'some_pass';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'ip_address';
```
If you see %, well then, there's another problem altogether as that is "any remote source". If however you do want any/all systems to connect via root, use the % wildcard to grant access:
```sh
CREATE USER 'root'@'%' IDENTIFIED BY 'some_pass';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
```
Finally, reload the permissions, and you should be able to have remote access:

FLUSH PRIVILEGES;
## [linux service ](http://www.cyberciti.biz/faq/centos-stop-start-restart-sshd-command/)  
CentOS turn on OpenSSH SSHD server on boot time command

The syntax is as follows to turn on SSHD on boot time:

# chkconfig sshd on
To turn off service on boot time, enter:

# chkconfig sshd off
To see the current status of service in each run-level type:

# chkconfig --list sshd
Sample outputs:

sshd           	0:off	1:off	2:on	3:on	4:on	5:on	6:off

CentOS start sshd service command

The syntax is:

# service sshd start
OR

# /etc/init.d/sshd start
CentOS stop sshd service command

The syntax is:

Alert: Do not run the following command over ssh based session and you will end up getting ‘network connectivity lost’ error.

# service sshd stop
OR

# /etc/init.d/sshd stop
CentOS restart sshd service command

The syntax is:

# service sshd restart
OR

# /etc/init.d/sshd restart
CentOS find status of the sshd service command

The syntax is:

# service sshd status
OR

# /etc/init.d/sshd status
Sample session outputs from the above commands
Fig. 01: service and chkconfig command in action

##[CentOS 配置防火墙操作实例（启、停、开、闭端口）](http://blog.csdn.net/jemlee2002/article/details/7042991)
CentOS 配置防火墙操作实例（启、停、开、闭端口）：
 
注：防火墙的基本操作命令：
查询防火墙状态:
[root@localhost ~]# service   iptables status<回车>
 
停止防火墙:
[root@localhost ~]# service   iptables stop <回车>
 
启动防火墙:
[root@localhost ~]# service   iptables start <回车>
 
重启防火墙:
[root@localhost ~]# service   iptables restart <回车>
 
永久关闭防火墙:
[root@localhost ~]# chkconfig   iptables off<回车>
 
永久关闭后启用:
[root@localhost ~]# chkconfig   iptables on<回车>
 
 
1、查看防火墙状态
[root@localhost ~]# service iptables status<回车> 

2、编辑/etc/sysconfig/iptables文件。我们实例中要打开8080端口和9990端口
用编辑器打开/etc/sysconfig/iptables 

3、依葫芦画瓢，我们添加8080端口和9990端口

4、保存/etc/sysconfig/iptables文件，并在终端执行
[root@localhost ~]# service iptables restart <回车>

5、从新查看防火墙状态
[root@localhost ~]# service iptables status<回车>

6、这时候，服务器的8080和9990端口就可以对外提供服务了。
7、其他端口的开放模式就是类似如此开放模式。
