---
title: "配置ssh"
date: 2024-08-17
weight: 120
description: >
  配置git以通过ssh的方式访问git仓库
---

为了在不同场合使用不同的 ssh key，或者是本地ssh登录时使用和代码仓库不一样的 ssh key，就需要设置让 git 支持多个 ssh key。

最常见的，需要准备两组ssh key：一个用来本地ssh登录避免输入密码麻烦，一个用来登录github。

## ssh登录的key

```bash
ssh-keygen -t rsa -C "localssh"
```

文件名默认id_rsa，不设置密码：

```bash
$ ssh-keygen -t rsa -C "localssh"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/sky/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/sky/.ssh/id_rsa
Your public key has been saved in /home/sky/.ssh/id_rsa.pub
```

这样就得到 id_rsa 和 id_rsa.pub 两个文件。

将 `.ssh/id_isa.pub` 文件到linux服务器端：

```bash
scp ~/.ssh/id_rsa.pub sky@192.168.0.10:/home/sky 
```

在ubuntu server服务器上运行：

```bash
mkdir -p .ssh
touch ~/.ssh/authorized_keys
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
```

以后简单输入 “ssh server.ip” 即可自动 SSH 登录不必输入密码。

## github的key

```bash
ssh-keygen -t rsa -C "github"
```

文件名默认id_rsa，不设置密码：

```bash
$ ssh-keygen -t rsa -C "github"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/sky/.ssh/id_rsa): id_rsa_github
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in id_rsa_github
Your public key has been saved in id_rsa_github.pub
```

这样就得到 id_rsa_github 和 id_rsa_github.pub 两个文件。将 id_rsa_github.pub 的内容提交到 github 即可使用。


## 参考资料

- https://segmentfault.com/a/1190000043924833