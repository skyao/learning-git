---
title: "修改注释"
linkTitle: "修改注释"
weight: 321
date: 2021-01-20
description: >
  在commit之后修改注释
---

## 已经 commit 但还没有 push

### 最近的一次commit

如果要修改 message 的是最近的一次 commit，则会简单很多，只要简单执行下面的命令修改：

```bash
git commit --amend -m "new commit message"
```

### 多条commit

如果要修改 message 的提交有多条，或者不是最新的一条，则要交互式变基（Interactive Rebase）。

先通过 git log 命令确认要修改 message 的 commit，比如是要修改倒数第3次的 commit，则可以执行：

```bash
git rebase -i HEAD~3
```

或者 `git rebase` 到需要修改的那个 commit 的前1个 commit。假设 commit id 是 32e0a87f，运行下面的`git rebase` 命令：

```bash
git rebase -i 32e0a87f
```

在 git bash 中运行上面的命令后，会弹出编辑框，在编辑框中会分行依次显示以 pick 开头的这个 commit 之后的所有 commit message。

将需要修改的 commit message 之前的 "pick" 改为 "reword"，点击保存按钮，并关闭编辑框，这时会执行rebase操作。

Rebasing (1/3)

接着会再次弹出编辑框，这次编辑框中只有之前改为 "reword" 的那个 commit message，此时修改 commit message 的内容，点击保存按钮并关闭编辑框，会继续执行 rebase 操作。

如果操作成功，会出现如下的提示：

```bash
[detached HEAD aa3b52c] Add return url
 2 files changed, 1 insertion(+), 3 deletions(-)
Successfully rebased and updated refs/heads/oss.
```

这样就完成了 git commit message 的修改，然后强制 push 一下就搞定了。注意可以一次性修改多条 commit，只要把多条 commit 之前的 "pick" 改为 "reword" 即可。

## 已经push到git仓库

修改 message 的方式是一样的，但是修改完之后需要强推才能覆盖远程仓库。

修改完成之后强推到 git 仓库：

```bash
# 如果是自己的仓库或者分支，不会有冲突问题，简单 --fore 即可
git push --force
# 如果是多人合作的仓库或者分支，需要使用更安全的版本：
git push --force-with-lease
```

关于 `--force` 和 `--force-with-lease` 的区别:

- `--force`：直接用本地的分支覆盖远程分支
- `--force-with-lease`：在覆盖前会检查一下远程分支有没有被别人提交了新代码。如果有新代码，强推会被拒绝，避免误删。



