# ubuntu 多jdk 版本设置默认版本

首先配置java环境  
有3个地方可以配置  
/etc/profile  
/etc/environment  
～/.bashrc  
网上解释很low 暂时忽略，如果配置/etc/profile 环境root 账户识别不了配置的jdk版本，所以我在系统环境
/etc/environment 里配置

```bash
export JAVA_HOME=/usr/local/jdk1.8.0_91
export CLASSPATH=..:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/local/jdk1.8.0_91/bin"

```
现在来看我电脑装了jdk版本
刚要查自己的jdk 配置的时候突然发现我的配置很low 就像上面配置的一样如果要使用不同的java 版本怎么办，网上查了一下找了一个好的建议：

[在linux下安装多个jdk版本](http://yusan.github.io/blog/2014/11/21/zai-linuxxia-an-zhuang-duo-ge-jdkban-ben/)

我重复一下   
1.首先这个是靠 /etc/alternatives/java 工具实现的（红帽中也有不过不叫这个 不知道是不是这个叫法，想当于系统环境配置 /etc/environment。  
2.
```bash
//查询当前jdk 配置
 sudo update-alternatives --display java

```
如图![](/assets/display_java.png)

我自己装了2个版本
```bash
 /usr/local/jdk1.7.0_60/bin/java - priority 300
 /usr/local/jdk1.8.0_91/bin/java - priority 300
```
openjdk 系统自己装的。

突然发现软件位置装错位置了 mv /usr/local/jdk* /usr/bin/ (移动位置)

重新配置jdk环境  
首先删除之前jdk 环境配置
```bash
sudo update-alternatives --remove java /usr/local/jdk1.8.0_91/bin/java
sudo update-alternatives --remove javac /usr/local/jdk1.8.0_91/bin/javac
sudo update-alternatives --remove java /usr/local/jdk1.7.0_60/bin/java
sudo update-alternatives --remove javac /usr/local/jdk1.7.0_60/bin/javac
```

3.重新配置jdk 到alternatives工具
```bash
 sudo update-alternatives --install /usr/bin/java java /usr/bin/jdk1.8.0_91/bin/java 300
 sudo update-alternatives --install /usr/bin/javac javac /usr/bin/jdk1.8.0_91/bin/javac 300
 sudo update-alternatives --install /usr/bin/java java /usr/bin/jdk1.7.0_60/bin/java 300
 sudo update-alternatives --install /usr/bin/javac javac /usr/bin/jdk1.7.0_60/bin/javac 300
```
  ![](/assets/jdk_configure.png)

4.查看当前java、javac 版本
![](/assets/java javac version.png)
                   <h2 style="text-align:center">当前版本 1.8.0_91 </h2>  

5.手动切换java javac版本
  alternatives --config java
  alternatives --config javac

结果  

 <h2 style="text-align:center">当前版本jdk1.7.0_60</h2>
