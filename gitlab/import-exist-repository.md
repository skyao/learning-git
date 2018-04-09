# 导入已有仓库

记录如何将现有的git reposotory导入到gitlab中.

##  前言

在使用 gitlab 之前, 我使用 gitolite 来保存自己私有的代码. 后来发现 gitlab 的功能远比 gitolite 要强大, 使用上也方便很多. 因此考虑放弃 gitolite, 而原有在 gitolite 中的代码就需要迁移过去, 同时希望能保留原有的 commit/tag/branch 等信息.

## 批量导入

发现 gitlab 对此有特别的支持, 而且支持多个仓库一起导入, 非常方便处理大批仓库的迁移.

> 参考官方文档： [Import bare repositories into your GitLab instance
](https://docs.gitlab.com/ee/raketasks/import.html)

假设我们有三个项目,a.git/b.git/c.git在gitolite中，我们准备将他们导入gitlab，放在名为backup的group中。则导入操作步骤如下:

1. 打包原有的bare reposotory

	注意一定要是**bare reposotory**。

	可以直接到git仓库的原始存储路径下打包，如：

	```bash
	cd /home/git/repositories/
    tar cvf code.tar a.git b.git c.git
    ```

	也可以通过带`--bare`参数的git clone命令来获取：

	```bash
	git clone --bare ××/a.git
	```

2. 在gitlab中为将要导入的项目做准备

	在gitlab的管理界面上添加一个名为backup的group.

3. 将打包后的文件传到目标机器上

4. 准备导入的目录结构

    ```bash
    # import目录下存放所有要导入的仓库，放在哪里无所谓
    mkdir /home/sky/import/
    # 建立子目录，对应要导入的group名
	mkdir /home/sky/import/backup

	# 将要导入的git仓库复制到子目录下
    cp -R a.git b.git c.git /home/sky/import/backup

	# 将整个import目录的owner和group都修改为git
    sudo chown -R git:git /home/sky/import/
	```

5. 执行导入命令

    ```bash
    # 注意这里的路径只到import路径，不要写子路径，子路径是用来制定group的
    sudo gitlab-rake gitlab:import:repos['/home/sky/import/']
    ```

	命令执行输出类似如下：

	```bash
    Processing /home/sky/import/backup/a.git
    * Using namespace: backup
    * Created a (backup/a-service)
    ```

成功之后就可以在gitlab的页面上看到新导入的git项目.

## 单个导入

先clone要迁移的仓库, clone的时候用--mirror参数来clone它的bare repository, 然后添加remote:

```bash
git clone --mirror git@192.121.166.180:root/ut-cidemo.git
cd ut-cidemo.git
git remote add gitlab git@basiccloud.net:lagency/ut-cidemo.git
git push -f --tags gitlab refs/heads/*:refs/heads/*
```

这个方式适合导入单个仓库。

