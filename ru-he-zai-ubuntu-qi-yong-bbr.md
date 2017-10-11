# [如何在 Ubuntu 启用 BBR\(参考该网址\)](https://gfw.press/blog/?p=7007)

\# 在 Ubuntu 启用 BBR 前，检查一下内核版本

uname -r

\# 如果输出看起来象 4.12.0-041200-generic，即内核版本为 4.9 或更高，则符合启用要求

\# 如果输出看起来象 3.13.0-125-generic，则首先需要升级内核

\# 在 Ubuntu 升级内核请参考[《如何升级 Ubuntu 内核》](https://gfw.press/blog/?p=6945)

\# 内核符合要求后，使用 vi 在 /etc/sysctl.conf 文件后添加两行配置

net.core.default\_qdisc = fq  
net.ipv4.tcp\_congestion\_control = bbr

\# 不会使用 vi 的纯菜鸟使用下面的命令添加

echo "net.core.default\_qdisc = fq" &gt;&gt; /etc/sysctl.conf  
echo "net.ipv4.tcp\_congestion\_control = bbr" &gt;&gt; /etc/sysctl.conf

\# 启用配置

sysctl -p

\# 恭喜你，你的 Ubuntu 服务器现在已经用上了 Google TCP BBR

