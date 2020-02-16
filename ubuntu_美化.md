## ubuntu 美化

### 1.常规软件
- 搜索软件 ag
```
sudo apt-get install silversearcher-ag
```
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
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
- 安装 zsh-completions 自动补全
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
### 3. tmux 相关
- 安装 tmux
```
sudo apt install tmux
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

