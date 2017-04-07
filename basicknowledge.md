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
cp /usr/share/zoneinfo/Asia/Shanghai  /etc/localtime
```



