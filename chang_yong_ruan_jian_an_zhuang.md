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

       sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

       // 选择 从bash 切换到zsh
       chsh -s `which zsh` 

       sudo shutdown -r 0

# Zathura PDF
```shell
sudo apt-get install zathura 

```
