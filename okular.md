安装

sudo apt-get install okular 大概10分钟

快捷键

F5 Reload

F6 打开注释

F7 导航栏

B 切换黑色背景模式，在幻灯片模式下有效

Ctrl + M Show Menubar

Ctrl + Shift + F 全屏

J 向下翻

K 向上翻

/ 搜索

F3 Find Next

Shift + F3 Find Previous

Ctrl + W 关闭当前pdf

Ctrl + Q 退出Okular

Ctrl + Shift + S 另存为

Ctrl + Z undo

Ctrl + Shift + Z redo

Ctrl + Shift + P 进入幻灯片

Ctrl + +/- 放大/缩小

Ctrl + G 跳到x页

Ctrl + Home 首页

Ctrl + End 尾页

Ctrl + 1-6 Browser Zoom Selection Text Table Magnifier

Alt + Shift + Left Back返回刚才查看的

Alt + Shift + Right Forward

Ctrl + B 添加Bookmarks

Ctrl + , Previous Tab

Ctrl + . Next Tab

Shift Scroll Down

Shift + Down Scroll Down

Shift + Up Scroll Up

Space Scroll Page Down 和 上一页不太一样

Shift + Space Scroll Page Up

自己设置快捷键

F2: Show Tool Bar

F4: Show Page Bar

F8: Show Forms

F9: Single Page

F10: Facing Page(Center First Page)双面模式

F11: Overview

F: Fit Page

W: Fit Width

N/P: Next/Previous Page

L/H: Next/Previous Bookmark Ctrl + B 添加的

Alt + Enter: Properties

Alt + 1: Configure Shortcuts

相关设置

注释文件.xml

Okular把标注的内容（划线，高亮，标记等）保存在一个xml文件中，该文件放在~/.kde/share/apps/okular/docdata/ 目录下，文件名格式为 一串数字+pdf文件名+.xml 。Okular 根据这个xml文件来显示标记内容，比如有个pdf文件 hello.pdf,标注完后即使把hello.pdf 移动到不同的目录下，再打开还是可以看到标记内容的，但是如果改了文件名，hello.pdf –> hell.pdf 就看不到标记的内容了。

背景颜色

Settings -> Configure Okular -> Accessibility(辅助功能) -> Change colors -> Color mode: Change Paper Color -> Paper color -> HTML: #d6e7cb

保存/配置快捷键

~/.kde/share/apps/okular/okularDefaultshortcuts.rc

有的话替换掉即可，没有就扔进去
