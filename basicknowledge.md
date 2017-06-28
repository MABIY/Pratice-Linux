#### ubuntu remove repository && remove ppas

```shell
vim /etc/apt/sources.list  # 修改 repository
rm -i /etc/apt/sources.list.d/myppa.list # 删除 ppas
```

### /var/lib/apt/lists huge

```shell
When you run sudo apt-get update (or use the Refresh button in a package manager), 
a list of packages will get downloaded from the Ubuntu servers.
These files are then stored in /var/lib/apt/lists/.

You can safely remove the contents of that directory as it is recreated
when you refresh the package lists.
If you remove the files, but do not run apt-get update to fetch the lists, 
commands like apt-cache will fail to provide information (since the cache is empty).
```

### ubuntu 设置时区

```shell
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

### [How can I remove icon of uninstalled application from application lens in Dash](https://askubuntu.com/questions/170468/how-can-i-remove-icon-of-uninstalled-application-from-application-lens-in-dash)

```shell
I had the same issue. First I uninstalled the application, then I deleted all references from the following folder:

/usr/share/applications
/usr/local/share/applications
~/.local/share/applications
Rebooted....

If not install this MENU editor:

sudo add-apt-repository ppa:caldas-lopes/ppa
sudo apt-get update
sudo apt-get install ezame
and delete unwanted icons.
```

# [How to restart X Window Server from command line?](https://askubuntu.com/questions/1220/how-to-restart-x-window-server-from-command-line)

```shell
sudo systemctl restart lightdm.service
```



#### To figure out which package provides a particular file, you can use`apt-file`\(install it by running`sudo apt install apt-file`\). For the case of`libQtWebKit.so.4`:

```
$ apt-file search libQtWebKit.so.4
libqtwebkit4: /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4
libqtwebkit4: /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4.10
libqtwebkit4: /usr/lib/x86_64-linux-gnu/libQtWebKit.so.4.10.2

```

If you prefer to use a web browser, go to[http://packages.ubuntu.com](http://packages.ubuntu.com/), search for`libQtWebKit.so.4`in "Search the contents of packages" and you will get:

```
File                                            Packages
/usr/lib/aarch64-linux-gnu/libQtWebKit.so.4     libqtwebkit4 [arm64]
/usr/lib/arm-linux-gnueabihf/libQtWebKit.so.4   libqtwebkit4 [armhf]
/usr/lib/i386-linux-gnu/libQtWebKit.so.4        libqtwebkit4 [i386]
/usr/lib/powerpc-linux-gnu/libQtWebKit.so.4     libqtwebkit4 [powerpc]
/usr/lib/powerpc64le-linux-gnu/libQtWebKit.so.4 libqtwebkit4 [ppc64el]
/usr/lib/s390x-linux-gnu/libQtWebKit.so.4       libqtwebkit4 [s390x]
/usr/lib/x86_64-linux-gnu/libQtWebKit.so.4      libqtwebkit4 [amd64]

```

  
  




