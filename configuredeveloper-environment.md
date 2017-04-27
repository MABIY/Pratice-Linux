### 开发环境配置 \(ubuntu\)

### /opt![](/assets/Screenshot from 2017-04-27 17-21-14.png)

### /opt/binray\_file \# 存放 源二进制文件 通过软链接 到 /opt 目录

![](/assets/Screenshot from 2017-04-27 17-22-50.png)

## 通过 update-alternatives 配置

```shell
➜  /opt sudo update-alternatives --display java
java - auto mode
  link best version is /opt/jdk1.8/bin/java
  link currently points to /opt/jdk1.8/bin/java
  link java is /usr/bin/java
/opt/jdk1.7/bin/java - priority 300
/opt/jdk1.8/bin/java - priority 400

```



