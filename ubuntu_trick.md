# ubuntu 技巧
## 1. 代理与取消代理

```
export http_proxy=127.0.0.1:12333
export https_proxy=127.0.0.1:12333
```

```
unset http_proxy
unset https_proxy
```

## 2. 远程开关科学上网

```
sudo electron-ssr
pkill electron-ssr
```

## 3. `curl` 下载不下来时换成 `wget`

## 4. `npm` 换淘宝的源。
```
npm config set registry https://registry.npm.taobao.org
```

## 5. `pip` 换国内的源
> https://blog.csdn.net/yuzaipiaofei/article/details/80891108
```
# 临时
pip install scrapy -i https://pypi.tuna.tsinghua.edu.cn/simple
```
```
# 永久
vim ~/.pip/pip.conf

[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```
```
# 源列表
阿里云 http://mirrors.aliyun.com/pypi/simple/ 
中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/ 
豆瓣(douban) http://pypi.douban.com/simple/ 
清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/ 
中国科学技术大学 http://pypi.mirrors.ustc.edu.cn/simple/
```

## 6. `go` 语言换源
> https://goproxy.io/zh/
```
# 启用 Go Modules 功能
export GO111MODULE=on

# 配置 GOPROXY 环境变量
export GOPROXY=https://goproxy.io
```

## 7. `docker` 镜像设置
> https://lug.ustc.edu.cn/wiki/mirrors/help/docker

```
sudo vim /etc/docker/daemon.json

# 网易的速度快
{
  "registry-mirrors": ["http://hub-mirror.c.163.com"]
}
```
## 8. 翻墙
1. 服务器端全局代理。
2. 设置中 `proxy` 选择 `auto`。
3. 浏览器测试是否成功。
4. 测试后远程重新打开 `SSH` 。


## 9. `vim`强制保存
```
:w !sudo tee %
:q!
```

## 10. 命令行记录错误信息
```
# 以docker中使用的方法为例
sudo docker-compose logs -f oiptestnet >> log.txt 
```

## 11. github中删除已经同步的.idea文件夹
```
git rm -r --cached .idea  #--cached不会把本地的.idea删除
git commit -m 'delete .idea dir'
git push -u origin master
```

## 12. vscode快捷键
- 跳转回之前的代码：
  alt + 左方向键
- 字体大小修改：
  ctrl -/+ 
