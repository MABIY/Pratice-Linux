在CentOS中，有三种定义的主机名:静态的（static），瞬态的（transient），和灵活的（pretty）。`静态`主机名也称为内核主机名，是系统在启动时从/etc/hostname自动初始化的主机名。`瞬态`主机名是在系统运行时临时分配的主机名，例如，通过DHCP或mDNS服务器分配。静态主机名和瞬态主机名都遵从作为互联网域名同样的字符限制规则。而另一方面，`灵活`主机名则允许使用自由形式（包括特殊/空白字符）的主机名，以展示给终端用户（如qqmm）。  
在CentOS 7中，有个叫hostnamectl的命令行工具，它允许你查看或修改与主机名相关的配置。

1. 要查看主机名相关的设置：

   ```
   [lh@min-study ~]$ hostnamectl status
      Static hostname: min-study
            Icon name: computer-vm
              Chassis: vm
           Machine ID: b198e03c64a141c3b5fa11f80097808b
              Boot ID: d514da06efd94d95865fc1c8283be827
       Virtualization: kvm
     Operating System: CentOS Linux 7 (Core)
          CPE OS Name: cpe:/o:centos:centos:7
               Kernel: Linux 3.10.0-514.el7.x86_64
         Architecture: x86-64
   ```

2. 只查看静态、瞬态或灵活主机名，分别使用`--static`，`--transient`或`--pretty`选项。

   ```
   [root@localhost ~]
   # hostnamectl --static

   localhost.localdomain
   [root@localhost ~]
   # hostnamectl --transient

   localhost.localdomain
   [root@localhost ~]
   # hostnamectl --pretty
   ```

3. 要同时修改所有三个主机名：静态、瞬态和灵活主机名：

   ```
   [root@localhost ~]
   # hostnamectl set-hostname qqmm

   [root@localhost ~]
   # hostnamectl --pretty

   [root@localhost ~]
   # hostnamectl --static

   qqmm
   [root@localhost ~]
   # hostnamectl --transient

   qqmm
   ```

   就像上面展示的那样，在修改静态/瞬态主机名时，任何特殊字符或空白字符会被移除，而提供的参数中的任何大写字母会自动转化为小写。  
   一旦修改了静态主机名，`/etc/hostname` 将被自动更新。然而，`/etc/hosts` 不会更新以保存所做的修改，所以你每次在修改主机名后一定要手动更新`/etc/hosts`，之后再重启CentOS 7。否则系统再启动时会很慢。

 4.如果你只想修改特定的主机名（静态，瞬态或灵活），你可以使用--static，--transient或--pretty选项。例如，要永久修改主机名，你可以修改静态主机名：

```shell
[root@localhost ~]# hostnamectl --static set-hostname qqmm
```



