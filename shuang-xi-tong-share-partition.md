## centos 7  install after win10

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
安装完成后 删除 logical  重新格式为 NTFS (fat32 单文件不能大于４ｇ)　在linux 中自动 mount
```

### three step 进入centos救援模式

```shell
sh-4.2# chroot /mnt/sysimage
sh-4.2# grub2-install /dev/vda
Installing for i386-pc platform.
Installation finished. No error reported.
sh-4.2# exit
sh-4.2# reboot
```

### four step  重启后进入linux system修改开机选单任务：

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

## ubuntu 17.04 install after win10 

### first partition install linux

```shell
LIVE  CD
[anaconda root@localhost /]# parted /dev/vda mklabel msdos            # 建立 MBR 分割
[anaconda root@localhost /]# parted /dev/vda mkpart primary 1M 2G     # 建立 /boot
[anaconda root@localhost /]# parted /dev/vda mkpart primary 2G 52G    # 建立 /
[anaconda root@localhost /]# parted /dev/vda mkpart primary 52G 152G  # 建立 C
[anaconda root@localhost /]# parted /dev/vda mkpart extended 152G 100%# 建立延伸分割
[anaconda root@localhost /]# parted /dev/vda mkpart logical 152G 100% # 建立逻辑分割
[anaconda root@localhost /]# parted /dev/vda print                    # 显示分割结果

INSTALL SYSTEM

```

### two step install window 10

```shell
安装完成后 删除 logical  重新格式为 NTFS (fat32 单文件不能大于４ｇ)　在linux 中自动 mount
```

### three step 通过Live CD恢复grub 引导

```shell
#Open the terminal and run 
sudo fdisk -l
#to see where Linux is installed.
#Run 
sudo mount /dev/sdaX /mnt   # sdax is /boot mount /dev/sdax
#where x is the number you have found Linux word in
#Run 
sudo grub-install --boot-directory=/mnt /dev/sdX 
sudo reboot
#进入ubuntu，update grub 获取win10 启动menu
sudo update-grub

#如果使用久的grub command  --> sudo grub-install --root-directory=/mnt /dev/sdX
# reboot 之后进入　
# grub> set root=hd0,msdos1  ## (hdX,Y) 是X磁盘的Y分区,分区从1开始计数,磁盘从0开始计数.
# grub> linux /vmlinuz-xxx-xxx root=/dev/sda2 ## 里边的xxxx可以按Tab键，如果有acpi问题,在最后加一句acpi=off,/dev/sda2 代表 linux安装目录
# grub> initrd /initrd.img-xxx-xxx
# grub> boot
# 加载内核　进入　ubunut
#to update grub
sudo update-grub
# 重建grub到第一硬盘mbr
sudo grub-install /dev/sda
sudo reboot


```



