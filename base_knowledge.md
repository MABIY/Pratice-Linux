### shell

```shel
cat  **/*mm  查看当前目录下递归 所有以mm 结尾的文件(include folder)
```

### 软链接配置

```shell
ln -s /home/lh/java/apache-maven-3.3.9/bin /home/lh/maven_bin
exprot PATH =$PATH:/home/lh/maven_bin
mvn -v --> Error: Could not find or load main class org.codehaus.plexus.classworlds.launcher.Launcher
 (bin 同级目录 boo目录下plexus-classworlds-2.5.2.jar 是一个类加载框架)

 它会寻找 软链接所在目录 链接脚本 应该也是一样 所以不可以直接配置 bin 的软链接 需要 配置 $MAVEN_HOME/bin 升级时只要替换
 $MAVEN_HOME 对应的链接就可以了
```

### shell 的执行方式

```shell
#!/bin/bash
cd /tmp
echo "hello,world!"

./echo.sh   使用 脚本上声明的 /bin/bash shell 执行 (一个新的会话 子 父会话等待其结束)
sh echo.sh  使用 /bin/sh 执行 (一个新的会话 子 父会话等待其结束)
source echo.sh 在当前shell 窗体中执行(一般配置文件修改在当前会话中起作用 使用source)
```

### 系统日志查看

```shell
journalctl -u service-name.service
```

### curl set proxy

```shell
curl --proxy http://127.0.0.1:36648 https://ajax.googleapis.com/ajax/libs/jquery/3.2.0/jquery.min.js -O
```



