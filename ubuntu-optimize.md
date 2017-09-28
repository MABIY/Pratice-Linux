#### [ubuntu optimize](https://itsfoss.com/speed-up-ubuntu-1310/)

##### 1.swapping change 

```shell
➜  ~ sudo vim /etc/sysctl.conf
+ vm.swappiness = 10

➜  ~ cat /proc/sys/vm/swappiness
```

##### 2.startup set

```shell
sudo sed –i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop （show hide startup application）
```



