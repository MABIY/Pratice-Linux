## ubuntu 开发环境搭建\(java\)

* jdk configuration  
* mvn configuration 
* mysql configuration
* Intellij IDEA configuration

### ubuntu bash application

```shell
/usr/share/applications
/usr/local/share/applications
~/.local/share/applications

如果重复安装软件没有在bash 里 现在这3个位置找 删除 重新启动 右击 到bash
```

### apt-file

```shell
sudo apt install apt-file  #搜索相关文件的包名
使用示例:
➜  ~ apt-file search libXext.so.6
libxext6: /usr/lib/x86_64-linux-gnu/libXext.so.6
libxext6: /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
libxext6-dbg: /usr/lib/debug/usr/lib/x86_64-linux-gnu/libXext.so.6.4.0

sudo apt install libxext6
```

### [apt-setting-proxy](https://help.ubuntu.com/community/AptGet/Howto)

```shell
export http_proxy=http://yourproxyaddress:proxyport
```

### sshpass

```shelll
sshpass -p 'password' rsync -a ccdb-wcp-portlet-1.0.0-SNAPSHOT.war wechat@11.29.163.215:/home/wechat

# sshpass 传递密码给使用ssh需要的密码的命令
```





