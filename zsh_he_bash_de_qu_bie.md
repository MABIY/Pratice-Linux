# zsh 和 bash 的区别

1.在完成JDK 的安装之后，还需要执行另外一个步骤: 把jdk/bin 目录添加到执行路径中。**所谓执行路径**是操作系统搜索本地可执行文件的目录列表。对于不同的操作系统，这个步骤的操作过程有所不同。
* 在UNIX （包括Linux、Mac OS X 和 Solaris）环境下，编辑执行路径的过程与所使用的shell 有关。如果使用的是Bourne Again shell（Linux 的默认选择），在~/bashrc 或 ～/.bash_profile 文件的末尾就要添加：
export PATH=jdk/bin：$PATH
