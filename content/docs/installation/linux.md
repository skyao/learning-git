---
title: "linux安装"
date: 2021-01-20
weight: 10
description: >
  在linux上安装Git
---

以下ubuntu版本验证OK：

- 16.04
- 20.04
- 22.04

以下debian版本验证OK：

- debian12

## 安装

为了拿到最新版本的 git,增加仓库然后再安装：

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git
```

安装完成之后，验证版本：

```bash
git --version
git version 2.43.0
```

此时 git 是在 /usr/bin/ 目录下：

```bash
root@sky2:~# which git
/usr/bin/git
root@sky2:~# ls -l /usr/bin/git
-rwxr-xr-x 1 root root 1920512 Oct  4 03:50 /usr/bin/git
```

## 参考资料

- [Installing Latest version of git in ubuntu](http://stackoverflow.com/questions/19109542/installing-latest-version-of-git-in-ubuntu)
