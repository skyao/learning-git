
---
title: "重命名分支"
linkTitle: "重命名分支"
weight: 311
date: 2021-01-20
description: >
  git中对现有分支进行重命名
---

## 本地操作

在本地 clone 好仓库之后, 执行分支的重命名操作, 如将默认分支从 mater 重命名为 main, 则需要执行如下命令:

```bash
# 确认在 master 分支上
# git checkout master

# 1. 本地进行分支重命名: master -> main
git branch -m main

# 2. 删除远程仓库的旧分支
git push origin --delete master

# 3. 推送新分支到远程仓库
git push origin -u main
```

对于其他位置 clone 的本地仓库, 则需要更新本地仓库:

```bash
# 获取最新变更
git fetch origin

# 删除本地旧分支
git branch -d master

# 切换到新分支并建立跟踪
git checkout --track origin/main
```

> 备注: 使用的 `-m` 是 `--move` 的简写

## github上操作

在 github 页面上操作重命名分支,如将默认分支从 mater 重命名为 main, 对于本地已经 clone 的仓库,则需要执行如下命令:

```bash
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```