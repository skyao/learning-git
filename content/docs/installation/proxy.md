---
title: "配置代理"
date: 2022-03-08
weight: 130
description: >
  配置git代理以加速访问
---

### linux 配置


`vi ~/.ssh/config`  打开文件（如果不存在则新建文件），内容如下：

```bash
# 这里必须是 github.com，因为这个跟我们 clone 代码时的链接有关
Host github.com
# 如果用默认端口，这里是 github.com，如果想用443端口，这里就是 ssh.github.com 详
# 见 https://help.github.com/articles/using-ssh-over-the-https-port/
HostName github.com
User git
# 如果是 HTTP 代理，把下面这行取消注释，并把 proxyport 改成自己的 http 代理的端>口
#ProxyCommand socat - PROXY:192.168.2.1:%h:%p,proxyport=7890
# 如果是 socks5 代理，则把下面这行取消注释，并把 6666 改成自己 socks5 代理的端口
ProxyCommand nc -v -x 192.168.2.1:7891 %h %p
```

### windows 配置

在 windows 下的 gitbash 中，由于没有 nc 命令，因此上面的命令会失败。需要替换为 connect 命令：

```bash
Host github.com
HostName github.com
User git
#ProxyCommand socat - PROXY:192.168.2.1:%h:%p,proxyport=7890
ProxyCommand connect -S 192.168.2.1:7891 %h %p
```
