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





