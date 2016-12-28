# centos7 自启动脚本
[Linux 运行等级。](https://www.ibm.com/developerworks/cn/linux/l-lpic1-v3-101-3/)  
运行级别  
运行级别 定义了在 Linux 系统的目前状态（或运行级别）下能够完成哪些任务。每个 Linux 系统支持三种基本的运行级别，以及完成正常操作所需的一个或多个运行级别。基本的运行级别如 表 1 中所示。
表 1. Linux 的基本运行级别
级别	目的
0	关闭（或停止）系统  
1	单用户模式；通常别称为 s 或 S  
6	重启系统  
除了这些基本的级别之外，运行级别使用还因版本不同而有所不同。一种常见的使用设置如 表 2 所示。  
表 2. 其他常见的 Linux 运行级别  
级别	目的  
2	没有联网的多用户模式  
3	联网的多用户模式  
5	联网并且使用 X Window 系统的多用户模式  
Slackware 发布版本对运行了 X Window 系统的整个系统使用了运行级别 4 而非 5。Debian 及其派生物，比如 Ubuntu，对所有的多用户模式使用了单一运行级别，通常为运行级别 2。请务必参考适用于您的发布版本的文档。


Linux Centos Automatically Start Apache Tomcat server on boot
This article assumes that you have already installed the Apache Tomcat Server on your Linux Centos machine. If you need help with your with Apache Tomcat Setup then please click on the Link below.
Install Apache Tomcat Server on Linux Centos 
  
Step 1: Create a file named tomcat6 in your /etc/init.d directory
$ cd /etc/init.d
$ gedit tomcat6 

Step 2: Copy the following script and save the file
#!/bin/bash
# chkconfig: 2345 80 20
# Description: Tomcat Server basic start/shutdown script
# /etc/init.d/tomcat6 -- startup script for the Tomcat 6 servlet engine

TOMCAT_HOME=/usr/local/apache-tomcat-6.0.35/bin
START_TOMCAT=/usr/local/apache-tomcat-6.0.35/bin/startup.sh
STOP_TOMCAT=/usr/local/apache-tomcat-6.0.35/bin/shutdown.sh

start() {
 echo -n "Starting tomcat6: "
 cd $TOMCAT_HOME
 ${START_TOMCAT}
 echo "done."
}

stop() {
 echo -n "Shutting down tomcat6: "
 cd $TOMCAT_HOME
 ${STOP_TOMCAT}
 echo "done."
}

case "$1" in
 
start)
 start
 ;;

stop)
 stop
 ;;

restart)
 stop
 sleep 10
 start
 ;;

*)
 echo "Usage: $0 {start|stop|restart}"

esac
exit 0

Change the settings for the chkconfig based on your requirements. In a scenario where Apache Web server is in the front of Tomcat server with MySQL database usually the startup sequence should be MySQL then Tomcat and Apache Web Server in last. Also make sure you change the TOMCAT_HOME, START_TOMCAT and STOP_TOMCAT variables based on your Tomcat Install.

Step 3: Update the file permissions to make it executable by any user
$ chmod 755 tomcat6

Step 4: Make sure you have chkconfig command installed
$ chkconfig --helpotherwise just install it
$ sudo apt-get install chkconfig
  
Step 5: Run chkconfig command to add the script to the startup services
$ chkconfig --add tomcat6

Basically the chkconfig command automatically adds the symbolic links for starting and stopping the service based on the paramaters passed to it. Here is the list of links created from the above link. You can run the find command to check.
$ find . -name "*tomcat6"

Response from the above command ...（没有出现）
./rc.d/init.d/tomcat6
./rc.d/rc4.d/S80tomcat6
./rc.d/rc3.d/S80tomcat6
./rc.d/rc6.d/K20tomcat6
./rc.d/rc5.d/S80tomcat6
./rc.d/rc2.d/S80tomcat6
./rc.d/rc0.d/K20tomcat6
./rc.d/rc1.d/K20tomcat6

Step 6: Make sure scripts got added to the startup services
Type the following command on the Terminal 
$ chkconfig --list tomcat6
Response should be something like this
tomcat6         0:off   1:off   2:on    3:on    4:on    5:on    6:off
  
Step 7: Verify your service is working
To start the Tomcat server
$ service tomcat start
To stop the Tomcat server
$ service tomcat stop

手写了２个shell :*
tomcat7_configurationb.sh
#!/bin/bash
chmod 755 /etc/init.d/tomcat6
chkconfig --add tomcat6
chkconfig --list tomcat6

del_tomcat7Configuration.sh
#!/bin/bash
chkconfig --del tomcat6

-------------------------------


概念　CHKCONFIG　->updates  and queries runlevel information for system ser-
       vices
chkconfig


CHKCONFIG(8)                                                      CHKCONFIG(8)




NAME

       chkconfig  -  updates  and queries runlevel information for system ser-
       vices



SYNOPSIS

       chkconfig --list [name]
       chkconfig --add name
       chkconfig --del name
       chkconfig [--level levels] name <on|off|reset>
       chkconfig [--level levels] name



DESCRIPTION

       chkconfig provides a  simple  command-line  tool  for  maintaining  the
       /etc/rc[0-6].d  directory  hierarchy by relieving system administrators
       of the task of directly manipulating the  numerous  symbolic  links  in
       those directories.

       This  implementation of chkconfig was inspired by the chkconfig command
       present in the IRIX operating system. Rather than maintaining  configu-
       ration  information  outside  of the /etc/rc[0-6].d hierarchy, however,
       this version directly manages  the  symlinks  in  /etc/rc[0-6].d.  This
       leaves  all  of  the  configuration information regarding what services
       init starts in a single location.

       chkconfig has five distinct functions: adding new services for  manage-
       ment,  removing  services  from management, listing the current startup
       information for services, changing the  startup  information  for  ser-
       vices, and checking the startup state of a particular service.

       When  chkconfig  is run without any options, it displays usage informa-
       tion.  If only a service name is given, it checks to see if the service
       is  configured to be started in the current runlevel. If it is, chkcon-
       fig returns true; otherwise it returns false. The --level option may be
       used  to  have  chkconfig query an alternative runlevel rather than the
       current one.

       If one of on, off, or reset is specified after the service  name,  chk-
       config  changes the startup information for the specified service.  The
       on and off flags cause the service to be started  or  stopped,  respec-
       tively,  in  the  runlevels  being  changed.  The reset flag resets the
       startup information for the service to whatever  is  specified  in  the
       init script in question.

       By  default,  the on and off options affect only runlevels 2, 3, 4, and
       5, while reset affects all of the runlevels.  The --level option may be
       used to specify which runlevels are affected.

       Note that for every service, each runlevel has either a start script or
       a stop script.  When switching runlevels, init  will  not  re-start  an
       already-started  service,  and  will  not re-stop a service that is not
       running.

       chkconfig also can manage xinetd scripts via the means of xinetd.d con-
       figuration  files.  Note that only the on, off, and --list commands are
       supported for xinetd.d services.



OPTIONS

       --level levels
              Specifies the run levels an operation should pertain to.  It  is
              given  as  a string of numbers from 0 to 7. For example, --level
              35 specifies runlevels 3 and 5.


       --add name

              This option adds a new  service  for  management  by  chkconfig.
              When  a new service is added, chkconfig ensures that the service
              has either a start or a kill entry in  every  runlevel.  If  any
              runlevel  is missing such an entry, chkconfig creates the appro-
              priate entry as specified by the  default  values  in  the  init
              script.  Note  that default entries in LSB-delimited ’INIT INFO’
              sections take precedence  over  the  default  runlevels  in  the
              initscript.


       --del name
              The  service  is removed from chkconfig management, and any sym-
              bolic links in /etc/rc[0-6].d which pertain to it are removed.

              Note that future package installs for this service may run  chk-
              config  --add,  which  will re-add such links. To disable a ser-
              vice, run chkconfig name off.


       --list name
              This option lists all of  the  services  which  chkconfig  knows
              about, and whether they are stopped or started in each runlevel.
              If name is specified, information in only display about  service
              name.



RUNLEVEL FILES

       Each  service which should be manageable by chkconfig needs two or more
       commented lines added to its init.d script. The first line  tells  chk-
       config  what  runlevels the service should be started in by default, as
       well as the start and stop priority levels. If the service should  not,
       by default, be started in any runlevels, a - should be used in place of
       the runlevels list.  The second line contains  a  description  for  the
       service,  and may be extended across multiple lines with backslash con-
       tinuation.

       For example, random.init has these three lines:
       # chkconfig: 2345 20 80
       # description: Saves and restores system entropy pool for \
       #              higher quality random number generation.
       This says that the random script should be started in levels 2,  3,  4,
       and 5, that its start priority should be 20, and that its stop priority
       should be 80.  You should be able to figure out  what  the  description
       says;  the \ causes the line to be continued.  The extra space in front
       of the line is ignored.



SEE ALSO

       init(8) ntsysv(8) system-config-services(8)



AUTHOR

       Erik Troan <ewt@redhat.com>





