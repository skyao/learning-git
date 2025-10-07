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
# for  github
Host github.com
    HostName github.com
    User git
    # for HTTP proxy
    #ProxyCommand socat - PROXY:192.168.0.1:%h:%p,proxyport=7890
    #ProxyCommand socat - PROXY:192.168.2.1:%h:%p,proxyport=7890
    #ProxyCommand socat - PROXY:192.168.3.1:%h:%p,proxyport=7890
    #ProxyCommand socat - PROXY:192.168.7.34:%h:%p,proxyport=7890
    # for socks5 proxy on linux
    #ProxyCommand nc -v -x 192.168.0.1:7891 %h %p
    #ProxyCommand nc -v -x 192.168.2.1:7891 %h %p
    #ProxyCommand nc -v -x 192.168.3.1:7891 %h %p
    #ProxyCommand nc -v -x 192.168.7.34:7891 %h %p
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github
```

### windows 配置

在 windows 下的 gitbash 中，由于没有 nc 命令，因此上面的命令会失败。需要替换为 connect 命令：

```bash
# for  github
Host github.com
    HostName github.com
    User git
    # for HTTP proxy
    #ProxyCommand socat - PROXY:192.168.0.1:%h:%p,proxyport=7890
    #ProxyCommand socat - PROXY:192.168.2.1:%h:%p,proxyport=7890
    #ProxyCommand socat - PROXY:192.168.3.1:%h:%p,proxyport=7890
    #ProxyCommand socat - PROXY:192.168.7.34:%h:%p,proxyport=7890
    # for socks5 proxy on windows
    #ProxyCommand connect -S 192.168.0.1:7891 %h %p
    #ProxyCommand connect -S 192.168.2.1:7891 %h %p
    #ProxyCommand connect -S 192.168.3.1:7891 %h %p
    #ProxyCommand connect -S 192.168.7.34:7891 %h %p
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github

# for xxxxxx company
Host xxxxxx.com
    HostName xxxxxx.com
    User git
    Port xxxx
    ProxyCommand socat - PROXY:proxy.xxxxxx.com:%h:%p,proxyport=xxxx
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_ed25519
```
