#### iscsi clinet :

```shell
yum install -y iscsi*

systemctl enabel iscsid

systemctl enable iscsi

vim /etc/iscsi/initiatorname.iscsi 
c:InitiatorName=iqn.2016-05.com.example:desktop10
:wq

systemctl start iscsid

iscsiadm --mode discoverydb --type sendtargets --portal 192.168.3.157 --discover

systemctl start iscsi

iscsiadm --mode node --targetname iqn.2016-05.com.example:server10 --portal 192.168.3.157:3260 --login

```



