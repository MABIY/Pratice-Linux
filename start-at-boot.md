#### vim /etc/rc.local  \(This script is executed at the end of each multiuser runlevel\)![](/assets/Screenshot from 2017-05-06 21-18-37.png)

#### Ubuntu is now using systemd, and rc.local is now considered a service which is turned "off"

#### the problem

If you type the following command in terminal:

```shell
sudo systemctl status rc-local
```

You may get this output:

```shell
● rc-local.service - /etc/rc.local Compatibility
 Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)
 Active: failed (Result: exit-code) since Thu 2015-11-26 23:54:58 CST; 59s ago
 Process: 1001 ExecStart=/etc/rc.local start (code=exited, status=1/FAILURE)
Nov 26 23:54:57 vivid rc.local[1001]: File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 920, in require
Nov 26 23:54:57 vivid rc.local[1001]: needed = self.resolve(parse_requirements(requirements))
Nov 26 23:54:57 vivid rc.local[1001]: File "/usr/lib/python2.7/dist-packages/pkg_resources/__init__.py", line 807, in resolve
Nov 26 23:54:57 vivid rc.local[1001]: raise DistributionNotFound(req)
Nov 26 23:54:57 vivid rc.local[1001]: pkg_resources.DistributionNotFound: shadowsocks==2.8.2
Nov 26 23:54:58 vivid sudo[1008]: pam_unix(sudo:session): session closed for user root
Nov 26 23:54:58 vivid systemd[1]: rc-local.service: control process exited, code=exited status=1
Nov 26 23:54:58 vivid systemd[1]: Failed to start /etc/rc.local Compatibility.
Nov 26 23:54:58 vivid systemd[1]: Unit rc-local.service entered failed state.
Nov 26 23:54:58 vivid systemd[1]: rc-local.service failed.
```

And if you try to enable /etc/rc.local to run on system boot with the command:

```shell
sudo systemctl enable rc-local
```

You may get:

```shell
The unit files have no [Install] section. They are not meant to be enabled
 using systemctl.
 Possible reasons for having this kind of units are:
 1) A unit may be statically enabled by being symlinked from another unit's
 .wants/ or .requires/ directory.
 2) A unit's purpose may be to act as a helper for some other unit which has
 a requirement dependency on it.
 3) A unit may be started when needed via activation (socket, path, timer,
 D-Bus, udev, scripted systemctl call, ...).
```

### The solution

As you can see from above, The unit file have no \[Install\] section. As such Systemd can not enable it. First we need to create a file:

```shell
sudo vim /etc/systemd/system/rc-local.service
```

Then add the following content to it.

```shell
[Unit]
 Description=/etc/rc.local Compatibility
 ConditionPathExists=/etc/rc.local

[Service]
 Type=forking
 ExecStart=/etc/rc.local start
 TimeoutSec=0
 StandardOutput=tty
 RemainAfterExit=yes
 SysVStartPriority=99

[Install]
 WantedBy=multi-user.target
```

Save and close the file. Make sure `/etc/rc.local`file is  exist and executable.

```shell
sudo touch /etc/rc.local && sudo chmod +x /etc/rc.local
```

After that, enable the service on system boot:

```shell
sudo systemctl enable rc-local
```

Output:

```shell
Created symlink from /etc/systemd/system/multi-user.target.wants/rc-local.service 
to /etc/systemd/system/rc-local.service.
```

Now start the service and check its status:

```shell
sudo systemctl start rc-local.service
sudo systemctl status rc-local.service
```

Output:

```shell
● rc-local.service - /etc/rc.local Compatibility
 Loaded: loaded (/etc/systemd/system/rc-local.service; enabled; vendor preset: enabled)
 Active: active (running) since Fri 2015-11-27 00:32:56 CST; 14min ago
 Process: 879 ExecStart=/etc/rc.local start (code=exited, status=0/SUCCESS)
 Main PID: 880 (watch)
 CGroup: /system.slice/rc-local.service
```

## Cron @reboot

f the above method does not work for you, or you just want some simple commands to be executed on system boot, then you can also use the @reboot feature in cron to automatically execute command on system boot. For example, I want my  [shadowsocks client](https://www.gitbook.com/book/liuhua/ubuntu/edit#) to auto start, so I open the root user’s cron file:

```shell
sudo crontab -e
```

And put the following line at the end of it.

```shell
@reboot /usr/bin/sslocal -c /etc/shadowsocks.json -d start
```

Save and close the file.

In some Linux distributions such as archlinux, the cron daemon is not enabled by default. So you have to manually enable it. To enable it on archlinux, enter the following command in the terminal.

```shell
sudo systemctl enable cronie
```

Shadowsocks is a socks5 proxy that can be used to bypass Internet firewalls, If you are interested, click the link below to learn how to setup your own shadowsocks server.

### 查看启动的服务

```shell
lh@lh-v:~$ ps aux | grep IntelliJIDEALicenseServer_linux_amd64 ### 查看进程pid
root       871  0.0  0.0   4496   788 ?        Ss   10:44   0:00 /bin/sh -c /home/lh/IntelliJIDEALicenseServer_linux_amd64
root       872  0.0  0.1   8648  7496 ?        Sl   10:44   0:00 /home/lh/IntelliJIDEALicenseServer_linux_amd64
lh        2790  0.0  0.0  21460  2728 pts/0    S+   10:45   0:00 grep --color=auto IntelliJIDEALicenseServer_linux_amd64

~$ sudo netstat -anp|grep 871
 # 查看启动的端口号 
 out:
  tcp        0      0 0.0.0.0:1017            0.0.0.0:*               LISTEN      872/IntelliJIDEALic 
  unix  3      [ ]         STREAM     CONNECTED     18720    1/init               /run/systemd/journal/stdout

 ~$ netstat -nplt
 (Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:1017            0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:5355            0.0.0.0:*               LISTEN      -                   
tcp6       0      0 :::22                   :::*                    LISTEN      -                   
tcp6       0      0 ::1:631                 :::*                    LISTEN      -                   
tcp6       0      0 :::5355
```

参考文章:

 [how to Enable /etc/rc.local with Systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)

    

