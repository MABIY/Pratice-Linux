#### when update ubuntu16.04 kernel to 4.13.0-26-generic  then systemctl hibernate not work -&gt; start up  screen not working

#### change grub2 use old kernel 4.10.0-42-generic

```shell
sudo vim /etc/default/grub

c: GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 4.10.0-42-generic"
```

or

```shell
sudo vim /etc/default/grub
c: GRUB_DEFAULT="1>3" 
#  1 -> Advanced options for Ubuntu 3->Ubuntu, with Linux 4.10.0-42-generic. start of 0 
:wq

```



