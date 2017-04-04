# 设置

## 打开设置

在菜单中打开 "Toos" -> "Options"：

![](images/settings/option-overview.jpg)

## 设置用户信息

### 设置默认用户信息

用户信息在每次提交/commit时都会附带上，以此来标志当前提交是谁提交的。

用户信息可以有两个层次：

1. 仓库级别的用户信息: 作用域仅仅限于当前仓库(repository)，不同仓库可以设置不同的信息。仓库级别的用户信息可以覆盖全局用户信息，如果仓库级别没有设置则取全局信息，如果都没有则提交时git会强制要求填写。
2. 全局(global)用户信息：也被成为默认用户信息(default user information)

"Options" 中可以设置默认用户信息，如图：

![](images/settings/user-information.jpg)

一般推荐在这里设置，如果某些仓库有特殊需要再在仓库级别单独设置。

### 设置仓库级别的用户信息

在菜单中打开 "Repository" -> "Repository Settings" -> "Advanced"：

![](images/settings/user-information2.jpg)

去掉"Use Global user settings"前面的勾选，就可以修改当前仓库级别的用户信息了。

## 设置 SSH

背景知识介绍: git 支持两种通讯方式，https和SSH：

- https: URL类似"https://github.com/skyao/leaning-git.git",这种方式要每次输入用户名密码（当然有些软件可以帮你记住用户名密码）
- SSH: "git@github.com:skyao/leaning-git.git"，这种方式只要设置好SSH key，每次操作不用再输入用户名密码

### 使用 OpenSSH 作为客户端

选择 OpenSSH 作为SSH客户端，然后SSH Key指向已经生成好的id_rsa：

![](images/settings/openssh.jpg)

### 使用 PuTTY 作为客户端

需要将 id_rsa 转一次得到 PuTTY key file，比较麻烦，一般推荐用 OpenSSH 。

## 仓库设置

![](images/settings/repository.jpg)

- Project folder: 设置默认的项目文件夹，在新建仓库/克隆仓库等操作时默认就会使用这个路径来保存新的仓库，如果不设置则windows下默认为当前用户的Documents目录。
- Language: 修改 sourcetree 界面的语言,推荐还是用英语吧，各种术语保持一致，用中文见面还需要中文英文对应过来。
- Default text encoding: 默认utf-8，一定不要改