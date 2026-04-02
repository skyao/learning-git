---
title: "checkout命令"
linkTitle: "checkout命令"
weight: 310
date: 2021-01-20
description: >
  checkout命令
---

### 从上流分支checkout

在不产生任何合并（Merge）和冲突的情况下，把 upstream（上游原仓库）的分支如 dev “搬”到个人 fork 仓库中。

先检查是否正确设置了 upstream：

```bash
git remote -v
```

如果没有，则通过命令添加 upstream：

```bash
git remote add upstream <原仓库的URL>
```

拉取 upstream 的信息:

```bash
git fetch upstream
```

基于远程 dev 分支创建本地 dev 分支：

```bash
git checkout -b dev upstream/dev
```

然后推动到自己的 fork 仓库：

```bash
git push -u origin dev
```

备注： -u 参数的意思是建立追踪关系，以后在本地的 dev 分支上执行 git push 或 git pull 时，Git 就会默认对应到 fork 仓库里的 dev 分支。