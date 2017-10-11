# 如何使用 Ubuntu 版大杀器

1.\# 本文介绍如何在 Ubuntu 下安装使用大杀器客户端，本次使用的是 Ubuntu 16，其它 Ubuntu 版本或其它 Linux 可参照安装使用。

\# 安装 git 工具  
sudo apt install git -y ;

\# 使用 git 获取大杀器  
sudo cd / ; sudo git clone https://github.com/chinashiyu/gfw.press ;

\# 给客户端脚本添加可执行属性  
sudo chmod +x /gfw.press/client.sh ;

\#安装 JAVA  
sudo apt install openjdk-8-jdk-headless -y ;

\# 运行大杀器  
sudo /gfw.press/client.sh ;

\# 配置节点

[![](https://gfw.press/blog/wp-content/uploads/2017/08/1.png)](https://gfw.press/blog/wp-content/uploads/2017/08/1.png)

\# 设置 Ubuntu 16 自带的 FireFox 浏览器代理

[![](https://gfw.press/blog/wp-content/uploads/2017/08/2.png)](https://gfw.press/blog/wp-content/uploads/2017/08/2.png)

\# 测试翻墙，非常成功

[![](https://gfw.press/blog/wp-content/uploads/2017/08/3.png)](https://gfw.press/blog/wp-content/uploads/2017/08/3.png)



石大爷，ubuntu启动报错阿。火狐一直测试失败。

初始化Cipher出错：  
java.security.InvalidKeyException: Illegal key size  
at javax.crypto.Cipher.checkCryptoPerm\(Cipher.java:1039\)  
at javax.crypto.Cipher.implInit\(Cipher.java:805\)  
at javax.crypto.Cipher.chooseProvider\(Cipher.java:864\)  
at javax.crypto.Cipher.init\(Cipher.java:1396\)  
at javax.crypto.Cipher.init\(Cipher.java:1327\)  
at press.gfw.Encrypt.encryptNet\(Encrypt.java:595\)  
at press.gfw.EncryptForwardThread.run\(EncryptForwardThread.java:119\)



JAVA 自带的加密包加密强度不够，需要下载加强包

[http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)



