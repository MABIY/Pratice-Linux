### Start configure for Java programmer with me on ubuntu

####1.配置jdk7 
  
  ```shell
  方法1:(都版本切换需要修改配置文件重启机器 "麻烦)
  有3个地方可以配置  
  /etc/profile   "对个人其作用
  /etc/environment  "对系统环境其作用 
  ～/.bashrc    "对打开的shell起作用,不同shell 文件不同 例如: oh-my-zsh 是 ~/.zshrc
  方法2:(推荐 方便切换多版本jdk)
  update-alternatives "使用该工具 在/usr/bin 寻找软连接命令 相当于系统环境配置 /etc/environment。
  
  ```
  
  #####方法1 操作:
  - 下载jdk-7u79-linux-x64.tar.gz
  - 下载jdk-8u111-linux-x64.tar.gz
  - 解压tar.gz 后路径 -> /opt/java/jdk1.7.0_79/  和 /opt/java/jdk1.8.0_111 
  ```shell
  sudo vi /etc/environment 
   
   ++ :/opt/java/jdk1.7.0_79/bin 在PATH内
   ++ export JAVA_HOME=/opt/java/jdk1.7.0_79
   ++ export CLASSPATH=..:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
   
   :wq
   
   source /etc/environment   "让该配置脚本在当前打开的shell 中其作用
        
  ```
   结果图片:
   
    ![jdk7-configure-complete](/assets/Screenshot from 2016-12-29 13-30-55.png)
    

   #####方法 2操作: [update-alternatives](http://yusan.github.io/blog/2014/11/21/zai-linuxxia-an-zhuang-duo-ge-jdkban-ben/)
   
   - 查询当前jdk 配置
   ```shell
   sudo update-alternatives --display java 

   ```
   我自己装了2个版本 ()
   如图![](/assets/display_java.png)
   ```shell
    /usr/local/jdk1.7.0_60/bin/java - priority 300
    /usr/local/jdk1.8.0_91/bin/java - priority 300
   ```
   首先删除之前jdk 环境配置 
   ```shell
    sudo update-alternatives --remove java /usr/local/jdk1.8.0_91/bin/java
    sudo update-alternatives --remove javac /usr/local/jdk1.8.0_91/bin/javac
    sudo update-alternatives --remove java /usr/local/jdk1.7.0_60/bin/java
    sudo update-alternatives --remove javac /usr/local/jdk1.7.0_60/bin/javac
   ```
   重新配置jdk 到alternatives工具
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

 
    
    
    
