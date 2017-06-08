# 导入已有仓库

记录如何将现有的 git reposotory 导入到 gitlab 中.

##  前言

在使用 gitlab 之前, 我使用 gitolite 来保存自己私有的代码. 后来发现 gitlab 的功能远比 gitolite 要强大, 使用上也方便很多. 因此考虑放弃 gitolite, 而原有在 gitolite 中的代码就需要迁移过去, 同时希望能保留原有的 commit/tag/branch 等信息.

## 导入bare repository

### 在gitlab服务器端批量导入

发现 gitlab 对此有特别的支持, 而且支持多个仓库一起导入, 非常方便处理大批仓库的迁移.

假设我们有三个项目,a.git/b.git/c.git在gitolite中, 导入 gitlab 的操作步骤如下:

1. 打包原有的bare reposotory

	```bash
	cd /home/git/repositories/
    tar cvf code.tar a.git b.git c.git
    ```

2. 在gitlab中为将要导入的项目做准备

	找到gitlab的配置文件gitlab.yml:

    ```bash
    sky@sky2:~$ sudo find / -name gitlab.yml
    /opt/gitlab/embedded/service/gitlab-rails/config/gitlab.yml
    /var/opt/gitlab/gitlab-rails/etc/gitlab.yml
    sky@sky2:~$ sudo vi /opt/gitlab/embedded/service/gitlab-rails/config/gitlab.yml
    ```

	打开找到下面内容, 主要是看repos_path的内容:

    ```bash
    ## GitLab Shell settings
    gitlab_shell:
    path: /opt/gitlab/embedded/service/gitlab-shell/

    # REPOS_PATH MUST NOT BE A SYMLINK!!!
    repos_path: /var/opt/gitlab/git-data/repositories
    ```

	默认 gitlab 在 `/var/opt/gitlab/git-data/repositories/` 目录下保存各个项目的 bare reposotory.

	gitlab 中对于项目存放的方式有两种:

    1. 项目属于某个用户, 比如 root/abc.git 项目,则保存路径为repositories/root/abc.git
    2. 项目属于某个group, 比如 group1/cde.git 项目, 则保存路径为gitlab-satellites/group1/cde.git

	为了管理方便这里我们将为原来的a/b/c三个项目建立一个group, 在gitlab的管理界面上添加一个名为backup的group.

3. 将打包后的文件传到目标机器上

	然后解压后放到/var/opt/gitlab/git-data/repositories/backup目录下,路径类似为gitlab-satellites/backup/a.git(同样还有b.git/c.git).

    执行命令:

	```bash
    sudo gitlab-rake gitlab:import:repos
    ```

    成功之后就可以在gitlab的页面上看到新导入的git项目.

## 用git命令在客户端单个导入

先clone要迁移的仓库, clone的时候用--mirror参数来clone它的bare repository, 然后添加remote:

```bash
git clone --mirror git@192.121.166.180:root/ut-cidemo.git
cd ut-cidemo.git
git remote add gitlab git@basiccloud.net:lagency/ut-cidemo.git
git push -f --tags gitlab refs/heads/*:refs/heads/*
```

# 导入已经clone的代码

如果已经从其他git仓库中clone下来代码, 则可以通过修改remote的方式来导入代码到gitlab项目中.

首先需要在gitlab上新建空项目, 然后:

```bash
git remote remove origin
git remote add origin git@basiccloud.net:lagency/ut-training.git
git push -u origin master
```

注: 如果有多个分支/tag怎么办? 还是上面的方法好用.

