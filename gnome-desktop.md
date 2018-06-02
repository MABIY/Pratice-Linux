### set  shortcuts

###### Keyboard---&gt; Windows

```
 View split on left : Alt+left 

 view split on right: Alt+ Right        

 HIde Window: Alt+ Down

 Maximize window : Alt+ up

 ➜  ~   gsettings set org.gnome.desktop.wm.keybindings panel-main-menu "[]" # disable Alt+F1

 keyboard (trash shorcuts set ) : nautilus trash:///
```

#### update gnome from 3.18 to 3.20

```shell
sudo add-apt-repository ppa:gnome3-team/gnome3-staging

sudo add-apt-repository ppa:gnome3-team/gnome3


sudo apt update


sudo apt dist-upgrade


sudo apt install gnome gnome-shell
```

#### Tweaks Extensions :

1. [Hide top bar ](https://extensions.gnome.org/extension/545/hide-top-bar/)
2. [AlternateTab](https://extensions.gnome.org/extension/15/alternatetab/)
3. [TopIcons Plus](https://extensions.gnome.org/extension/1031/topicons/)
4. [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
5. [Workspace Grid](https://extensions.gnome.org/extension/484/workspace-grid/)

#### sougou-input方法

```shell
vim /etc/profile
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS=@im=fcitx
```

#### 字体设置

```shell
sudo apt install ttf-wqy-microhei
```

#### 效果图片

![](/assets/ubuntu_gnome.png)

