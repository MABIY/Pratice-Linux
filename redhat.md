#### selinux :

```shell
[root@rh100 ~]# getenforce  #查看状态

[root@rh100 ~]# vim /etc/selinux/config   #配置文件

[root@rh100 ~]# echo 0 > /sys/fs/selinux/enforce  #设置运行状态为permissive
```

#### mandb:

```shell
[lh@r110 ~]$ sudo mandb  # 安装用户手册    
```



