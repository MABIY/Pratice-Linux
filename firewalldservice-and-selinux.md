## 关闭centos 7 firewalld.service

```shell

systemctl disable firewalld.service : 开机禁用firewalld.service

systemctl enable firewalld.service : 开机启动firewalld.service

```

---

## 关闭selinux

```shell

getenforce ： 查看selinux 状态

setenforce 0 : 临时关闭selinux

setenforce 1 : 临时开启selinux

vim /etc/selinux/config : 开机禁用selinux

SELINUX=disabled

```
