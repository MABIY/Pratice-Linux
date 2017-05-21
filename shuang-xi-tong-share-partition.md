### first partition install linux

```shell
[anaconda root@localhost /]# parted /dev/vda mklabel msdos            # 建立 MBR 分割
[anaconda root@localhost /]# parted /dev/vda mkpart primary 1M 2G     # 建立 /boot
[anaconda root@localhost /]# parted /dev/vda mkpart primary 2G 52G    # 建立 /
[anaconda root@localhost /]# parted /dev/vda mkpart primary 52G 152G  # 建立 C
[anaconda root@localhost /]# parted /dev/vda mkpart extended 152G 100%# 建立延伸分割
[anaconda root@localhost /]# parted /dev/vda mkpart logical 152G 100% # 建立逻辑分割
[anaconda root@localhost /]# parted /dev/vda print                    # 显示分割结果
```

### two step install window 10

```shell
删除  格式化 logical 
```

### three 救援模式

```shell

sh-4.2# chroot /mnt/sysimage
sh-4.2# grub2-install /dev/vda
Installing for i386-pc platform.
Installation finished. No error reported.
sh-4.2# exit
sh-4.2# reboot
```

### 修改开机选单任务：

```shell
[root@study ~]# vim /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7" {
   set root='(hd0,3)'
   chainloader +1
}

[root@study ~]# vim /etc/default/grub
GRUB_TIMEOUT=30  # 将 5 秒改成 30 秒长一些
...
[root@study ~]# grub2-mkconfig -o /boot/grub2/grub.cfg
```



