#### 隐藏默认启动项，设置显示时间为0 

```shell
vim /etc/default/grub

+ GRUB_FORCE_HIDDEN_MENU="true"
e GRUB_TIMEOUT=0

```



