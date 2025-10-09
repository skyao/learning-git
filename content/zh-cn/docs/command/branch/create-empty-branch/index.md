---
title: "创建空白分支"
linkTitle: "创建空白分支"
weight: 311
date: 2021-01-20
description: >
  git中创建新的空白分支
---

在偶尔的情况下，可能会想要保留那些与你的代码没有共同祖先的分支。例如在这些分支上保留生成的文档或者其他一些东西。

如果需要创建一个不使用当前代码库作为父提交的分支，可以用如下的方法创建一个空分支。

## 方法1

执行以下git命令：

```bash
git symbolic-ref HEAD refs/heads/newbranch
rm .git/index
git clean -fdx
<do work>
git add your files
git commit -m 'Initial commit'
```

## 方法2

这里以github的操作为例，下面试图创建一个名为gh-pages的空分支：

```bash
$ cd repo

$ git checkout --orphan gh-pages
# 创建一个orphan的分支，这个分支是独立的
Switched to a new branch 'gh-pages'

$ git rm -rf .
# 删除原来代码树下的所有文件
rm ......
```

## 添加内容并push

注意这个时候用git branch命令是看不见当前分支的名字的，除非进行了第一次commit。

下面我们开始添加一些代码文件，例如这里新增了一个index.html:

```bash
$ echo \"My GitHub Page\" > index.html
$ git add .
$ git commit -a -m \"First pages commit\"
$ git push origin gh-pages
```

在commit操作之后，你就可以用git branch命令看到新分支的名字了，然后push到远程仓库。