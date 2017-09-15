**      为何2&gt;&1要写在后面？**

      command &gt; file 2&gt;&1 

       首先是command &gt; file将标准输出重定向到file中， 2&gt;&1 是标准错误拷贝了标准输出的行为，也就是同样被重定向到file中，最终结果就是标准输出和错误都被重定向到file中。 

      command 2&gt;&1 &gt;file 

      2&gt;&1 标准错误拷贝了标准输出的行为，但此时标准输出还是在终端。&gt;file 后输出才被重定向到file，但标准错误仍然保持在终端。

