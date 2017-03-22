### [理解linux 系统的负荷](http://www.ruanyifeng.com/blog/2011/07/linux_load_average_explained)

```shell
➜  ~ uptime   # 分别是一分钟 ,5分钟,15 分钟
 14:24:16 up 50 min,  1 user,  load average: 0.61, 0.89, 0.91

 ➜  ~ cat /proc/cpuinfo  # 查看CPU信息
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 71

➜  ~ grep -c 'model name' /proc/cpuinfo  # 返回CPU的总核心数
8
```



