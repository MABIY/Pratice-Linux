＃learn 山丘

```

１．vim /etc/selinux/config (配置selinux)　　
２．cat !$ (查看上一次中的参数，编辑文件之后可以看)　
//关闭防火墙　
3.　iptable -F 
    /etc/init.d/iptables save
4. echo $? （查看上面的命令时候执行了）
5.恢复被删除目录 
  tar jxvf extundelete-0.2.4.tar.bz2
  cd extundelete-0.2.4
  yum install -y  e2fsprogs-devel
  make && install
  卸载分区(防止继续写入)
  extundelete /dev/sda4 --inode 2 （查看节点深度文件）
  extundelete  /dev/sda4 --restore-inode  12（根据inode 恢复）
  extundelete /dev/sda4 --restore-file  passwd（根据文件名）
  extundelete  /dev/sda4 --restore-all （恢复所有文件）

pm -ivh /mnt/Packages/lrzsz-0.12.20-27.1.el6.x86_64.rpm



通过iconv命令转码

输入/输出格式规范： -f, --from-code=名称 原始文本编码  
 -o, --output=FILE 输出文件
 -l, --list 列举所有已知的字符集
 [root@xuegod63 test]# iconv -f gb2312 c.txt -o ssss.txt

 [root@xuegod63 test]# cat ssss.txt



 解决将公司服务器上脚本导到windows上打开串行的问题

 这是因为windows和linux处理回车不同。

 unix2dos b.txt



```

