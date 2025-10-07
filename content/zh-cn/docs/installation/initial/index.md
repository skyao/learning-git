---
title: "初始化配置"
date: 2021-01-20
weight: 110
description: >
  配置git的基本信息
---

### 查看 git 配置

安装之后，使用下面的命令查看 git 的配置：

```bash
$ git config --list

credential.helper=osxkeychain
user.name=Sky Ao
user.email=aoxiaojian@gmail.com
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
core.ignorecase=true
core.precomposeunicode=true
remote.origin.url=git@github.com:skyao/learning-git.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.master.remote=origin
branch.master.merge=refs/heads/master
remote.docsy.url=git://github.com/skyao/docsy-example.git
remote.docsy.fetch=+refs/heads/*:refs/remotes/docsy/*
```

### 配置全局的name和email

使用下面的命令设置全局的用户 name 和 email ：

```bash
git config --global --edit
```

然后修改里面的内容，设置好 name 和 email：

```properties
# This is Git's per-user configuration file.
[user]
# Please adapt and uncomment the following lines:
name = Sky Ao
email = aoxiaojian@gmail.com
```

也可以通过下面两条命令来分别设置：

```bash
git config --global user.name "Sky Ao"
git config --global user.email "aoxiaojian@gmail.com"
```

上面两个方式都是修改全局配置文件，默认地址是 `~/.gitconfig`，可以直接通过 vi 等命令打开修改。

### 配置单个仓库的name和email

如果有某个仓库需要设置和默认全局用户不一样的 name 和 email，则可以通过如下命令：

```bash
git config user.name "aoxiaojian"
git config user.email "aoxiaojian@gmail.com"
```

通过可以通过命令 `git config --list` 进行查看，配置内容同样存放在文件  `~/.gitconfig` 中。

### 参考资料

- [How to Configure Git Username and Email Address | Linuxize](https://linuxize.com/post/how-to-configure-git-username-and-email/)
- [Git - First-Time Git Setup (git-scm.com)](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)