#### at && notify-send "test"

```shell
➜  ~ sudo apt install -y at #安装at 一次性定时 daemon
➜  ~ at 15:00 
➜  ~ at 15:11
warning: commands will be executed using /bin/sh
at> notify-send "买菜"        
at> <EOT>
job 5 at Thu Sep 21 15:11:00 2017
```

#### [crontab && notify-send "test"](https://askubuntu.com/questions/834476/how-to-use-notify-send-with-crontab)

```shell
As suggested by @Lnux:

Create a .sh, for example test.sh:

#!/bin/sh
eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";

#Code:
DISPLAY=:0 notify-send "Test"
Then set up crontab:

crontab -e
And at the bottom, add:

* * * * * /home/myUser/test.sh
Obs.: you can place your .sh file in another location and don't forget to allow executing it.
```



