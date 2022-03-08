---
title: "配置代理"
date: 2022-03-08
weight: 130
description: >
  配置git代理以加速访问
---



`vi ~/.ssh/config`  打开文件（如果不存在则新建文件），内容如下：

```bash
# 这里必须是 github.com，因为这个跟我们 clone 代码时的链接有关
Host github.com
# 如果用默认端口，这里是 github.com，如果想用443端口，这里就是 ssh.github.com 详
# 见 https://help.github.com/articles/using-ssh-over-the-https-port/
HostName github.com
User git
# 如果是 HTTP 代理，把下面这行取消注释，并把 proxyport 改成自己的 http 代理的端>口
#ProxyCommand socat - PROXY:127.0.0.1:%h:%p,proxyport=3333
# 如果是 socks5 代理，则把下面这行取消注释，并把 6666 改成自己 socks5 代理的端口
ProxyCommand nc -v -x 192.168.0.1:23456 %h %p
```

