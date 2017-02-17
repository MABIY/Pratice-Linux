#### Find 

```
find -name 1    #默认在当前目录查找


find /home/lh  -size +1024c -a -size -5120c -type f  #准确大小在1024c 到5120c 不包含开始结束 类型规则文件 f

find . -size +1024c -a -size -5120c -exec ls -l {} \; # 显示详细

find /etc -size +50k -a ! -user root  #表示字节大于50k -a 便是并且 创建着不是root


find /etc/ -size +1500k -o -size 0k  # k 不能完全匹配使用 'c' for bytes 命令表示大于1500k 或 等于Ok



```



