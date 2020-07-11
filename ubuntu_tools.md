## ubuntu 美化
```
# apt 软件一步安装
sudo apt install silversearcher-ag autojump fzf tree htop curl wget git zsh fonts-powerline tmux vim gcc make pkg-config autoconf automake python3-docutils libseccomp-dev libjansson-dev libyaml-dev libxml2-dev python3-pip
```


### 1. 常规软件
~~- (windows)先安装字体 DejaVu Sans Mono for Powerline.ttf~~

~~```https://github.com/yanglr/WindowsDevTools/tree/master/awosomeTerminal/fonts-Ubuntu```~~

~~```https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/DejaVuSansMono```~~

- (`windows`)安装 `powerlevel10k` 字体 `MesloLGS` (本文件夹有备份)
```
https://github.com/romkatv/powerlevel10k#meslo-nerd-font-patched-for-powerlevel10k
```

- (`windows`) `Mobaxterm` 修改字体

```
https://blog.csdn.net/qingliang4321/article/details/104040593
```
> `terminal type` 选择 `xterm-256color`

- (`windows`) `windows terminal` 选择设置->`"profiles"`->`"list"`->`{}`中加入
```
,
"fontFace":"MesloLGS NF",
"fontSize":12
```

- `ubuntu/windows` 双系统时间不同步
```
timedatectl set-local-rtc 1 --adjust-system-clock
```
- 搜狗输入法
```
sudo apt install fcitx
sudo dpkg -i sogou*.deb
```
> 1. 移步到设置-区域和语言，加入汉语。
> 2. 管理已安装的语言，修改键盘输入法系统为 `fcitx` 。
> 3. 打开所有程序，选择 `Fcitx` 配置，加号添加搜狗输入法。
- 网易云音乐
```
https://music.163.com/#/download
```
- `VPN` 软件 `EASY CONNECT`
```
https://vpn.nwpu.edu.cn
```
> 登录后显示下载页面
- 文献阅读软件 `Mendeley`
```
https://www.mendeley.com/download-desktop-new/#download
```
> 1. 选择 `Tools` -> `Options` -> `Connection`
> 2. `Proxy type` 为 `HTTP Proxy`
> 3. `Server 127.0.0.1`
> 4. `Port 12333`
- 搜索软件 `ag`
```
sudo apt install silversearcher-ag
```
- 搜索软件 `autojump`
```
sudo apt install autojump
```
- 模糊搜索 `fzf`
```
sudo apt install fzf
```
```
# 若安装失败
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```
- 树形结构文件夹
```
sudo apt install tree
```
- 进程监控软件 `htop`
```
sudo apt install htop
```
### 2. `zsh` 相关
- 下载软件 `curl` 和 `wget`
```
sudo apt install curl
sudo apt install wget
```
- 安装 `git`
```
sudo apt install git
git config --global user.name "GuoxiW"
git config --global user.email "guoxiwang1996@gmail.com"
```
- `git` 公钥绑定 `github`
```
mkdir ~/.ssh/
cd ~/.ssh/
ssh-keygen -t rsa -C "guoxiwang1996@gmail.com"
(github加入后)
ssh -T git@github.com
```

- 安装 `zsh`
```
sudo apt install zsh
````
- 安装 `oh-my-zsh` 的字体
```
sudo apt install fonts-powerline
```
- 安装 `oh-my-zsh`
```
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
~~- (上一步通常可以)切换 `zsh` 为默认 `shell`~~

~~```chsh -s /bin/zsh/```~~

~~or~~

~~```chsh -s $(which zsh)```~~

- 配置密码文件，解决 `chsh: PAM` 认证失败的问题
```
sudo vim /etc/passwd
```
> 把第一行的 `/bin/bash` 改成 `/usr/bin/zsh` ，这个是 `root` 用户的。
- 安装 `powerlevel10k` 主题
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```
- 安装 `zsh-syntax-highlighting` 语法高亮
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
- 安装 `zsh-history-substring-search` 历史记录命令提示
```
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
```
- 安装 `zsh-autosuggestions` 语法历史记录
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
- 安装 `zsh-completions` 自动补全
```
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-completions
```
- 替换 `.zshrc`
```
mkdir ~/Documents
cd ~/Documents
git clone https://github.com/GuoxiW/linux_configuration
cp linux_configuration/.zshrc ~/.zshrc
cp linux_configuration/.p10k.zsh ~/.p10k.zsh
```
- (如果不是 `wsl` 就注释掉)解决 `windows terminal` 进 `wsl` 时目录不是 `/home`，在 `~/.zshrc` 最后加入 
```
if [ `pwd` = "/mnt/c/Users/wang9" ]; then
cd ~
fi
```
- (如果是 `aws` )更改 `ZSH` 路径
```
export ZSH="/home/ubuntu/.oh-my-zsh"
```
- 定制 `powerlevel10k`
```
source ~/.zshrc
```
or
```
p10k configure
```
### 3. `tmux` 相关
- 安装 `tmux`
```
sudo apt install tmux
```
- 安装 `Oh My Tmux`
```
cd
git clone https://github.com/gpakosz/.tmux.git
ln -s -f .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
```
- 注释掉 `ctrl + b c` 新开一个 `session` 的快捷键（默认是新开一个 `window` ）
```
vim ~/.tmux.conf
```
- 如果此时 `tmux` 不能正常显示，可能是因为有正在运行的 `tmux session`
```
tmux kill-server
```
### 4. `vim` 相关
- 安装 `vim`
```
sudo apt install vim
```
- 安装 `vim` 包管理软件 `vim-plug`
```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
- 安装代码浏览软件需要的插件
> https://github.com/universal-ctags/ctags/blob/master/docs/autotools.rst 

```
sudo apt install gcc make pkg-config autoconf automake python3-docutils libseccomp-dev libjansson-dev libyaml-dev libxml2-dev
```

```
cd ~/Documents
git clone https://github.com/universal-ctags/ctags
cd ctags
```

```
./autogen.sh
./configure --prefix=/usr/local #/where/you/want # defaults to /usr/local
make
sudo make install # may require extra privileges depending on where to install
```
- 安装 `vim` 代码补全的插件
```
sudo apt-get install python3-pip
pip3 install --user pynvim -i https://pypi.tuna.tsinghua.edu.cn/simple
```
- 复制 `.vimrc`
```
cd ~/Documents
git clone https://github.com/GuoxiW/linux_configuration
cp linux_configuration/.vimrc ~/.vimrc
```
- `vim-plug` 安装插件，打开 `vim`
```
:PlugInstall
```
- `vim-hybrid` 主题本身由 `vim-plug` 安装，如果没成功
```
cd ~/Documents
git clone https://github.com/w0ng/vim-hybrid
mkdir ~/.vim/colors/
cp vim-hybrid/colors/hybrid.vim ~/.vim/colors/hybrid.vim
```
- `coc.nvim` 需要的 `node.js`
```
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs npm
```
- `vim markdown` 的浏览器配置
```
let g:mkdp_path_to_chrome = "/usr/bin/google-chrome" 
```

- 设置 `vim` 运行 `c++` 需要的配置
```
cd ~/Documents
cp linux_configuration/vim_cpp_tasks.ini ~/.vim/tasks.ini
```
- `vim` 代码补全 `coc.nvim` 所需要的额外安装
```
:CocInstall coc-snippets 
```
- `vim` 版本更新
```
sudo add-apt-repository ppa:jonathonf/vim
sudo apt-get update
sudo apt-get install vim
```
### 5. 字体美化(放大)
- 在 `terminal` 中选择 `preferences` 
- 更改字体为 `Source Code Pro for Powerline Medium` ,　字号为 `20` 

### 6. 安装 `docker` 环境
1. 安装 `docker engine`
> https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io

```

2. 安装 `docker compose`
> https://docs.docker.com/compose/install/
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo curl -L https://raw.githubusercontent.com/docker/compose/1.25.5/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose
```

启动 `docker`

```
sudo service docker start
```

设置 `docker` 开机自启动
```
sudo systemctl enable docker.service
```

3. `docker` 镜像设置
> https://lug.ustc.edu.cn/wiki/mirrors/help/docker

```
sudo vim /etc/docker/daemon.json
# 网易的速度快
{
  "registry-mirrors": ["http://hub-mirror.c.163.com"]
}
```

4. 删除所有 `docker` 容器
```
sudo docker rmi $(sudo docker images -a -q)
```

### 7. 安装 go
1. 下载软件包
> https://golang.org/dl/

2. 解压
```
sudo tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

3. 加入 PATH
```
sudo vim /etc/profile
```
```
export PATH=$PATH:/usr/local/go/bin
```

### 8. 安装 Mysql
> https://blog.csdn.net/qq_41420747/article/details/96706274
1. 安装 Mysql 
```
# ETDB 是 Mysql 5.7.21 Ubuntu 18.04的默认版本
# 用 wsl 安装会出现问题。
sudo apt install mysql-server
```

2. 配置 Mysql
```
sudo mysql -uroot -p
```
```
CREATE USER 'guoxi'@'%' IDENTIFIED BY '123456';
flush privileges;
grant all on *.* to 'guoxi'@'%';
flush privileges;
```
