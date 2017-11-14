# 常用软件安装

### shadowsocks-qt5 install

```
  sudo add-apt-repository ppa:hzwhuang/ss-qt5
  sudo apt-get update
  sudo apt-get install shadowsocks-qt5

  配置自动启动
  startup set：
  name:Shadowsocks-Qt5
  command:/usr/bin/ss-qt5
  comment:/usr/bin/ss-qt5
```

# Oh My Zsh

    sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

       // 选择 从bash 切换到zsh
       chsh -s `which zsh` 

       sudo shutdown -r 0

# Zathura PDF

```shell
sudo apt-get install zathura
```

# [2 Best Chinese PinYin Input Method in Ubuntu 16.04](http://ubuntuhandbook.org/index.php/2016/07/2-best-chinese-pinyin-im-ubuntu-16-04/)

## googlepinyin

```shell
sudo apt install fcitx fcitx-googlepinyin fcitx-table-wbpy fcitx-pinyin fcitx-sunpinyin
```

## sougou

```shell
sudo apt remove fcitx* && sudo apt autoremove
sudo dpkg -i ~/Downloads/sogoupinyin*.deb; sudo apt -f install
```

#### [youtobe-Downloader](https://www.ubuntuupdates.org/ppa/getdeb_apps?dist=xenial)

```shell
wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu xenial-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'
sudo apt-get install youtube-dl
sudo apt install -y ytd-gtk
```

#### 



