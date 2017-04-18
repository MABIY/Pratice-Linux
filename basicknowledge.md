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



