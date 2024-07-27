---
title: "配置ssh"
date: 2021-01-20
weight: 120
description: >
  配置git以通过ssh的方式访问git仓库
---

为了方便日常使用，推荐采用ssh的方式来clone git仓库。

为此，需要创建 ssh key 并配置。

## 创建 ssh key

```bash
ssh-keygen -t rsa
```

一路回车确认，最后成功生成，创建的 ssh key 文件位于 `~/.ssh/id_rsa.pub`：

```bash
$ ls -l ~/.ssh
total 8
-rw------- 1 sky sky 1679 Oct 26 15:24 id_rsa
-rw-r--r-- 1 sky sky  396 Oct 26 15:24 id_rsa.pub
```

id_rsa.pub 是 ssh 的公钥，后面配置时要提交的公钥的内容就在这个文件中。

## github 配置

登录之后，点红色箭头所指处，下拉菜单中点 "settings"， 然后点 "SSH and GPG keys" -> "New SSH key"，最后将 id_rsa.pub 文件的内容复制过来提交：

![](images/add_key_github.jpg)

配置完成之后，尝试以ssh方式执行git clone 命令：

```bash
git clone git@github.com:skyao/learning-git.git
```

