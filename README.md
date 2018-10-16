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

<image src="./images/git-submodule.png"/>

## clone 一个带子模块的项目

1. clone 主仓库

```shell
➜  ~ git clone https://github.com/hbxeagle/git-submodule-main.git
Cloning into 'git-submodule-main'...
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 11 (delta 0), reused 11 (delta 0), pack-reused 0
Unpacking objects: 100% (11/11), done.
➜  ~ cd git-submodule-main
➜  git-submodule-main git:(master) ll
total 8
-rw-r--r--  1 didi  staff   1.4K Oct 16 15:21 README.md
drwxr-xr-x  2 didi  staff    64B Oct 16 15:21 git-submodule-one
drwxr-xr-x  3 didi  staff    96B Oct 16 15:21 images
➜  git-submodule-main git:(master) ll git-submodule-one
```
2. 执行 `git submodule init` 初始化本地配置文件。

```shell
➜  git-submodule-main git:(master) git submodule init
Submodule 'git-submodule-one' (https://github.com/hbxeagle/git-submodule-one.git) registered for path 'git-submodule-one'
```

3. 执行 `git submodule update` 来从子项目拉取所有数据，并检出你上层项目里所列的合适的提交。

```shell
➜  git-submodule-main git:(master) git submodule update
Cloning into '/Users/didi/Workspace/WorkspaceGithub/OwnBack/git-submodule-main/git-submodule-one'...
Submodule path 'git-submodule-one': checked out 'd1d9d7464948f4b5c64ceaf3a745f01f25fa8579'
➜  git-submodule-main git:(master) ll git-submodule-one
total 8
-rw-r--r--  1 didi  staff    20B Oct 16 15:22 README.md
```
<image src="./images/git-submodule-clone.png"/>

## 开发

## 更新代码

## merge 子模块冲突

## 移除子模块