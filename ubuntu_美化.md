## ubuntu 美化

### 1.常规软件
- 搜索软件 ag
```
sudo apt-get install silversearcher-ag

- 搜索软件 autojump
```
sudo apt install autojump
```
- 模糊搜索 fzf
```
sudo apt install fzf
```
### 2. zsh相关
- 下载软件 curl 和 wget
```
sudo apt install curl
sudo apt install wget
```
- 安装 git
```
sudo apt install git
```
- 安装 zsh
```
sudo apt install zsh
````
- 切换 zsh 为默认 shell
```
chsh -s /bin/zsh/
```
- 配置密码文件，解决chsh: PAM认证失败的问题
```
sudo vim /etc/passwd
```
把第一行的/bin/bash改成/bin/zsh，这个是root用户的。
- 安装 oh-my-zsh 的字体
```
sudo apt install fonts-powerline
```


