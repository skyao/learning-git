安装
===========

## 安装 Git

后面具体介绍如何在各个操作系统中安装git。

## 配置ssh key

### 创建 ssh key

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

### github 配置

登录之后，点红色箭头所指处，下拉菜单中点 "settings"， 然后点 "SSH and GPG keys" -> "New SSH key"，最后将 id_rsa.pub 文件的内容复制过来提交：

![](images/add_key_github.jpg)


git clone git@github.com:basiccloud/basiccloud-site.git

### gitlab 配置

TBD