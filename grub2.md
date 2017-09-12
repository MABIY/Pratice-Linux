#### [隐藏默认启动项，设置显示时间为0](https://wiki.archlinux.org/index.php/GRUB_%28%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%29)

```shell
vim /etc/default/grub  (虚拟机里这样设置，生产环境不可以)

+ GRUB_FORCE_HIDDEN_MENU="true"
e GRUB_TIMEOUT=0
```



