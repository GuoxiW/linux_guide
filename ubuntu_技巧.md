# ubuntu 技巧
## 1.代理与取消代理

```
export http_proxy=127.0.0.1:12333
export https_proxy=127.0.0.1:12333
```

```
unset http_proxy
unset https_proxy
```

## 2.远程开关科学上网

```
sudo electron-ssr
pkill electron-ssr
```
