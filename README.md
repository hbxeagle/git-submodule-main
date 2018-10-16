# git-submodule-main

> [Git 工具 - 子模块](https://git-scm.com/book/zh/v1/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97)

## 添加一个子模块

子模块名称：git-submodule-one
子模块Git仓库地址：https://github.com/hbxeagle/git-submodule-one.git

1. `clone` 目标仓库到当前目录
2. 执行 `git submodule add` 将该项目加为子模块
```shell
➜  git-submodule-main git:(master) ✗ git submodule add https://github.com/hbxeagle/git-submodule-one.git
Adding existing repo at 'git-submodule-one' to the index
```
3. 查看项目修改
```shell
➜  git-submodule-main git:(master) ✗ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   .gitmodules
	new file:   git-submodule-one
```
4. 查看 `submodule` 配置
```shell
➜  git-submodule-main git:(master) ✗ cat .gitmodules
[submodule "git-submodule-one"]
	path = git-submodule-one
	url = https://github.com/hbxeagle/git-submodule-one.git
```
5. 提交修改
```shell
➜  git-submodule-main git:(master) ✗ git commit -m 'first commit with submodule git-submodule-one'
[master 594e007] first commit with submodule git-submodule-one
 2 files changed, 4 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 git-submodule-one
```

<image src="./images/git-submodule.png" width="50%" height="50%"/>