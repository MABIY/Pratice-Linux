# Idea 2016.1 ubuntu 中文字体显示
下载自己想要的字体微软雅黑 等。

sudo mkdir /usr/share/fonts/truetype/yahei
sudo cp yahei.ttf  /usr/share/fonts/truetype/yahei
fc-cache -f -v

清空idea 缓存：  
    File->invalidate cache\restart  
设置字体  
    File->setting   
                 Editor->colors&Fonts>font   
                    勾选Secondary Font：选择Microsoft YaHei(之前安装的字体)  

               可能 之后清空项目数据后无法正常显示在idea 里重新配置就可以了。

突然发现还是有乱码  
    需要在 appearance 中覆盖默认字体，改成 刚刚在  
     Editor->colors&Fonts>font 选的中文字体，经过这两部就可以了  
     不过没有原来的漂亮，字体显示影响美观    

   ### 最后决定 安装文泉驿微黑字体库

     sudo  apt  install ttf-wqy-microhei





   ![结果图](/assets/22.png)




   ![效果图](/assets/.png)
