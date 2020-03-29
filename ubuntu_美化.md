## ubuntu 美化

### 1.常规软件
- ubuntu/windows 双系统时间不同步
```
timedatectl set-local-rtc 1 --adjust-system-clock
```
- 搜狗输入法
```
sudo apt install fcitx
sudo dpkg -i sogou*.deb
```
> 1. 移步到设置-区域和语言，加入汉语。
> 2. 管理已安装的语言，修改键盘输入法系统为 fcitx 。
> 3. 打开所有程序，选择 Fcitx 配置，加号添加搜狗输入法。
- 网易云音乐
```
https://music.163.com/#/download
```
- VPN 软件 EASY CONNECT
```
https://vpn.nwpu.edu.cn
```
> 登录后显示下载页面
- 文献阅读软件 Mendeley
```
https://www.mendeley.com/download-desktop-new/#download
```
> 1. 选择 Tools -> Options -> Connection
> 2. Proxy type 为 HTTP Proxy
> 3. Server 127.0.0.1
> 4. Port 12333
- 搜索软件 ag
```
sudo apt install silversearcher-ag
```
- 搜索软件 autojump
```
sudo apt install autojump
```
- 模糊搜索 fzf
```
sudo apt install fzf
```
- 树形结构文件夹
```
sudo apt install tree
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
git config --global user.name "GuoxiW"
git config --global user.email "guoxiwang1996@gmail.com"
```
```
cd ~/.ssh/
ssh-keygen -t rsa -C "guoxiwang1996@gmail.com"
(github加入后)
ssh -T git@github.com
```

- 安装 zsh
```
sudo apt install zsh
````
- 切换 zsh 为默认 shell
```
chsh -s /bin/zsh/
```
or
```
chsh -s $(which zsh)
```
- 配置密码文件，解决chsh: PAM认证失败的问题
```
sudo vim /etc/passwd
```
> 把第一行的/bin/bash改成/bin/zsh，这个是root用户的。
- 安装 oh-my-zsh 的字体
```
sudo apt install fonts-powerline
```
- 安装 oh-my-zsh
```
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
- 安装 zsh-syntax-highlighting 语法高亮
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
- 安装 zsh-history-substring-search 历史记录命令提示
```
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
```
- 安装 zsh-autosuggestions 语法历史记录
```
git clone git://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
- 安装 zsh-completions 自动补全
```
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-completions
```
- 替换 zshrc
```
vim ~/.zshrc
```
> https://github.com/GuoxiW/linux_configuration/blob/master/.zshrc
### 3. tmux 相关
- 安装 tmux
```
sudo apt install tmux
```
- 安装 Oh My Tmux
```
cd
git clone https://github.com/gpakosz/.tmux.git
ln -s -f .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
```
- 注释掉 ctrl + b c 新开一个 session 的快捷键（默认是新开一个 window ）
```
vim ~/.tmux.conf
```
### 4. vim 相关
- 安装 vim
```
sudo apt install vim
```
- 安装 vim 包管理软件 vim-plug
```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
- 安装代码浏览软件需要的插件
> https://github.com/universal-ctags/ctags/blob/master/docs/autotools.rst 

```
sudo apt install \
    gcc make \
    pkg-config autoconf automake \
    python3-docutils \
    libseccomp-dev \
    libjansson-dev \
    libyaml-dev \
    libxml2-dev
```

```
git clone https://github.com/universal-ctags/ctags
```

```
./autogen.sh
./configure --prefix=/usr/local #/where/you/want # defaults to /usr/local
make
make install # may require extra privileges depending on where to install
```
- 安装 vim 代码补全的插件
```
pip3 install --user pynvim 
```

- vim markdown 的浏览器配置
```
let g:mkdp_path_to_chrome = "/usr/bin/google-chrome" 
```

- 设置 vim 运行 c++ 需要的配置
```
linux_configuration/vim_cpp_tasks.ini    ---->>>>>    ~/.vim/tasks.ini
```
- vim 代码补全 coc.nvim 所需要的额外安装
```
:CocInstall coc-snippets 
```
### 5. 字体美化(放大)
- 在 terminal 中选择 preferences 
- 更改字体为 Source Code Pro for Powerline Medium ,　字号为 20 
