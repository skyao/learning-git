---
title: "解决can't push错误"
linkTitle: "解决can't push错误"
weight: 357
date: 2021-01-22
description: >
  通过set-url解决can't push错误
---

如果clone时 remote 的地址信息有问题，比如通过 `git clnoe git://github.com/skyao/learning-git.git` 的方式 clone 下来的仓库，在改动之后push时，会报错，错误信息如下：

```bash
git push
fatal: 远程错误：
  You can't push to git://github.com/skyao/learning-git.git
  Use https://github.com/skyao/learning-git.git
```

事实上，在github 页面上，给出的clone地址是 

```bash
git@github.com:skyao/learning-git.git
git@github.com/skyao/learning-git.git
```

和前面clone下来时使用的地址仅有一个字符的差异。

解决问题的方法，可以重新用正确的地址再clone一遍。如果已经有commit，则可以使用 remote 的 set-url 子命令直接修改remote的地址：

```bash
git remote set-url origin git@github.com:skyao/learning-git.git
sky@B-47WAMD6R-0023 learning-git % git push
Connection to github.com port 22 [tcp/ssh] succeeded!
```

### 参考资料

- https://stackoverflow.com/questions/42735837/git-bash-remote-error-you-cant-push-to-git-github-com