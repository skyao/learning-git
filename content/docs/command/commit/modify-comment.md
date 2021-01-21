---
title: "修改注释"
linkTitle: "修改注释"
weight: 321
date: 2021-01-20
description: >
  在commit之后修改注释
---

## 已经 commit 但还没有 push

TBD

## 已经 push

对于已经提交并已经 push 到远程仓库中的需要通过 `git rebase` 才能完成。

首先要 `git rebase` 到需要修改的那个 commit 的前1个 commit。假设 commit id 是 32e0a87f，运行下面的`git rebase` 命令：

```bash
git rebase -i 32e0a87f
```

在 git bash 中运行上面的命令后，会弹出编辑框，在编辑框中会分行依次显示以 pick 开头的这个 commit 之后的所有 commit message。

将需要修改的commit message之前的"pick"改为"reword"，点击保存按钮，并关闭编辑框，这时会执行rebase操作。

Rebasing (1/3)

接着会再次弹出编辑框，这次编辑框中只有之前改为"reword"的那个commit message，此时修改commit message的内容，点击保存按钮并关闭编辑框，会继续执行rebase操作。

如果操作成功，会出现如下的提示：

```bash
[detached HEAD aa3b52c] Add return url
 2 files changed, 1 insertion(+), 3 deletions(-)
Successfully rebased and updated refs/heads/oss.
```

这样就完成了git commit message的修改，然后强制push一下就搞定了。

```bash
git push --force
```

## 参考资料

- http://www.cnblogs.com/dudu/p/4705247.html
- https://help.github.com/articles/changing-a-commit-message/
- [快速批量修改Git提交注释方法](http://www.kaijia.me/2014/01/fast-way-to-batch-edit-git-commit-message/)



