### Start configure for Java programmer with me on ubuntu

####1.配置jdk7 
  
  ```shell
  有3个地方可以配置  
  /etc/profile   "对个人其作用
  /etc/environment  "对系统环境其作用 
  ～/.bashrc    "对打开的shell起作用,不同shell 文件不同 例如: oh-my-zsh 是 ~/.zshrc

  ```
  - 下载jdk-7u79-linux-x64.tar.gz
  - 加压目录后jdk7路径 -> /opt/java/jdk1.7.0_79/
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
