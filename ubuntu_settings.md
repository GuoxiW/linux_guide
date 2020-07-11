# `ubuntu` 配置

## 1. `ubuntu` 不要最小安装，容易缺失文件；

## 2. 不要勾选自动登录，会出现循环登陆的现象，如果出现非显卡原因的循环登录
> https://www.cnblogs.com/tengge/p/12774341.html
```
Control + Alt + F3
```

## 3. 换源

> https://developer.aliyun.com/mirror/ubuntu?spm=a2c6h.13651102.0.0.53322f70iuzkz2

	sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
	sudo gedit /etc/apt/sources.list

---
`Ubuntu 18.04`

	deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse

	deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse

	deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse

	deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse

	deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

---
`Ubuntu 20.04`

	deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse

	deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse

	deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
	
	deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse

	deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
	deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
---

## 4. 安装 `ifconfig` 并关闭多余的网卡。
```
sudo apt install net-tools
```
```
ifconfig
ifconfig eno2 down
```

## 5. 推荐 `pppoeconf` 拨号上网，校园网不容易掉线~~也可以使用拨号。~~
```
sudo apt install pppoeconf
```

`pppoe` 网络不稳定
```
sudo vi /etc/ppp/options
```

```
lcp-echo-failure 400
lcp-echo-interval 3
```

~~拨号参考链接：~~

~~> https://jingyan.baidu.com/article/59a015e37dbea2f79588655c.html~~

## 6. 安装 `openssh-server`

	sudo apt install openssh-server
	sudo update-rc.d ssh defaults

## 7. `ssh` 免密码登录

- `windows` 下生成密钥
	
```
ssh-keygen -t rsa -C "guoxiwang1996@gmail.com"
```

- 在 `ubuntu` 开启自动认证功能

```
sudo vim /etc/ssh/sshd_config
```

去掉注释

	RSAAuthentication yes 
	PubkeyAuthentication yes 
	AuthorizedKeysFile .ssh/authorized_keys

- `ubuntu` 中加入 `windows` 公钥

```
sudo vim ~/.ssh/authorized_keys # 复制本地的 C:\Users\wang9\.ssh\id_rsa.pub
```

- `windows` 配置自动认证，在 `C:\Users\wang9\.ssh\` 下新建 `config` 文件
```	
Host b
User guoxi
Hostname 10.69.12.250
IdentityFile C:\Users\wang9\.ssh\id_rsa
```
- 以后使用时

```
ssh b
```
- `vscode` 安装 `Remote SSH` 进行开发

## 8. 开启屏幕共享

 > https://blog.csdn.net/weixin_33804990/article/details/92484727

`ubuntu 20.04` 不能识别 `pppoe` 拨号上网，所以不能打开屏幕共享，此时通过手机共享网络后打开。

## 9. 更新显卡驱动解决循环登陆问题
```
#  关闭用户图形界面
sudo systemctl set-default multi-user.target
sudo reboot

# 安装显卡驱动
sudo bash N..

# 开启用户图形界面
sudo systemctl set-default graphical.target
sudo reboot
```

## 10. 翻墙

### 安装依赖

```
sudo apt install libcanberra-gtk-module libcanberra-gtk3-module gconf2 gconf-service libappindicator1 libssl-dev libsodium-dev python
```

### 安装软件

```
sudo dpkg -i  *.deb
```

### 尝试运行软件

终端输入

```
electron-ssr
```

看有没有什么报错，如果没有，就在软件里面设置订阅地址看能否更新。<br>
因为终端信息会泄露我的IP，密码，在这里我就不放内容。<br>
请确保没有报错并可以成功更新节点<br>

> *手动退出软件重启系统（笑，Windows习惯）*

**注意：如果到这里你可以使用软件正常的代理就无需进行下一步!!!**

### 系统设置

完成上一步之后并不能实现代理
在启动器中找到系统设置-网络设置-网络代理设置为如下图所示

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/2.png?raw=true)

上诉设置需要与软件中的设置一样（端口）

### 开始上网
选择节点-选择上网模式
到这里我已经可以pac上网或全局上网

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/3.png?raw=true)

测试pac是否代理成功——百度“ip”

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/4.png?raw=true)

测试全局是否代理成功——百度“ip”

![](https://github.com/qingshuisiyuan/electron-ssr-backup/blob/master/img/ubuntu/5.png?raw=true)

### 系统自动代理

在系统设置-网络设置-代理设置改为自动一样可用

（笑，系统设置那一步白设置了？）

不，在某些Debian系列中，你还真得手动设置，自动无效

本应用使用 `gsetting` 设置系统代理，所以有些Linux系统无法使用该功能

### 某些软件提示https错误

如git就提示过

具体原因不知道

尝试使用以下方法解决：

1. 更改系统代理方式为自动
2. 使用 `pac`

## 11. 修改 `github` 的 `hosts`
> https://www.cnblogs.com/huangzs/p/12765284.html

> https://site.ip138.com/
```
sudo vim /etc/hosts
```

```
# GitHub Start
52.74.223.119 github.com
192.30.253.119 gist.github.com
54.169.195.247 api.github.com
185.199.111.153 assets-cdn.github.com
151.101.76.133 raw.githubusercontent.com
151.101.108.133 user-images.githubusercontent.com
151.101.76.133 gist.githubusercontent.com
151.101.76.133 cloud.githubusercontent.com
151.101.76.133 camo.githubusercontent.com
151.101.76.133 avatars0.githubusercontent.com
151.101.76.133 avatars1.githubusercontent.com
151.101.76.133 avatars2.githubusercontent.com
151.101.76.133 avatars3.githubusercontent.com
151.101.76.133 avatars4.githubusercontent.com
151.101.76.133 avatars5.githubusercontent.com
151.101.76.133 avatars6.githubusercontent.com
151.101.76.133 avatars7.githubusercontent.com
151.101.76.133 avatars8.githubusercontent.com
# GitHub End
```

## 12. 解决 `AWS` 总是很快断开连接
```
sudo vim /etc/ssh/sshd_config
```
去掉注释并修改
```
# ClientAliveInterval 0
# ClientAliveCountMax 3
```
```
# 客户端每隔多少秒向服务发送一个心跳数据
ClientAliveInterval 30
# 客户端多少秒没有相应，服务器自动断掉连接
ClientAliveCountMax 1800
```
```
sudo service sshd restart
```

## 13. `AWS` 中设置账户密码
```
sudo passwd ubuntu
```
## 14. 阿里云中新建账户 `guoxi` 并给与 `sudo` 权限
```
sudo adduser guoxi
```
```
sudo vim /etc/sudoers
```
```
# root 之后添加
root    ALL=(ALL:ALL) ALL
guoxi   ALL=(ALL:ALL) ALL
```
```
# 如果不能保存
:w !sudo tee %
:q!
```

## 15. VMware 虚拟机驱动
```
sudo apt install open-vm-tools
sudo apt install open-vm-tools-desktop
```
## 16. windows terminal 的 wsl 操作
- 查看安装的 wsl

	wslconfig /list

- 设置默认子系统

	wslconfig /setdefault Name

- 打开特定子系统

	ubuntu1804.exe
	ubuntu2004.exe
