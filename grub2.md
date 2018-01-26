#### [隐藏默认启动项，设置显示时间为0](https://wiki.archlinux.org/index.php/GRUB_%28简体中文%29)

```shell
vim /etc/default/grub  (虚拟机里这样设置，生产环境不可以)

+ GRUB_FORCE_HIDDEN_MENU="true"
e GRUB_TIMEOUT=0

➜  ~ grub2-mkconfig -o /boot/grub2/grub.cfg
```

#### [修改启动默认显示时间](https://www.ssdax.com/2347.html)

```shell
#GRUB_DEFAULT="0"
GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 4.10.0-42-generic"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
```



