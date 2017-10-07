#### iscsi server:

##### 1.installl targetcli packaget

```shell
[root@localhost ~]# yum install -y targetcli

[root@localhost ~]# systemctl enable target;  systemctl start target;

[root@localhost ~]# firewall-cmd --permanent --add-port=3260/tcp;firewall-cmd --reload
```

##### 2.lvm create  lv block

##### ![](/assets/Screenshot from 2017-10-07 23-54-20.png)![](/assets/Screenshot from 2017-10-07 23-58-32.png)

##### 3. targetcli create target

![](/assets/Screenshot from 2017-10-08 00-04-02.png)

#### iscsi clinet :

##### 1.connection iscsi target

```shell
yum install -y iscsi-initiator-utils

[root@localhost ~]# systemctl enable iscsid iscsi

vim /etc/iscsi/initiatorname.iscsi 
c:InitiatorName=iqn.2016-05.com.example:desktop10
:wq


[root@localhost ~]# man iscsiadm

[root@localhost ~]# iscsiadm --mode discoverydb --type sendtargets --portal 192.168.3.157 --discover

[root@localhost ~]# systemctl restart iscsid iscsi

[root@localhost ~]# iscsiadm --mode node --targetname iqn.2017-10.com.example:server10 --portal 192.168.3.157:3260 --login
```

##### 2. fdisk block && mkfs.xfs && automount

![](/assets/Screenshot from 2017-10-08 00-27-20.png)

```shell
[root@localhost ~]# mkfs.xfs /dev/sdb5
[root@localhost ~]# vim /etc/fstab 
+ UUID="48903d6d-095c-44b5-93e2-ddd745aba453" /iscsi      xfs     defaults,_netdev        0 0
:wq
mount -a
```

when iscsi client have problem : see [websit](https://unix.stackexchange.com/questions/207534/iscsi-login-failed-with-error-24-could-not-log-in-to-all-portals)

