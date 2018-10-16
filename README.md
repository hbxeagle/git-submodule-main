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
### 修改主项目代码
按正常流程，add、commit、push

### 修改子项目代码
1. 在子项目目录，按正常流程，add、commit、push
```shell
➜  git-submodule-one git:(master) ✗ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
➜  git-submodule-one git:(master) ✗ git commit -am "修改 Readme，测试子模块提交修改"
[master 66cd3cc] 修改 Readme，测试子模块提交修改
 1 file changed, 1 insertion(+), 1 deletion(-)
➜  git-submodule-one git:(master) git push -u origin master
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 355 bytes | 355.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/hbxeagle/git-submodule-one.git
   a6a2e51..66cd3cc  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```
2. 切换到主项目目录，提交子项目的commit
```shell
➜  git-submodule-one git:(master) cd ..
➜  git-submodule-main git:(master) ✗ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   git-submodule-one (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
➜  git-submodule-main git:(master) ✗ git add .
➜  git-submodule-main git:(master) ✗ git commit -m "提交子模块修改"
[master 07c7f3b] 提交子模块修改
 1 file changed, 1 insertion(+), 1 deletion(-)
➜  git-submodule-main git:(master) git push -u origin master
Counting objects: 2, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 268 bytes | 268.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/hbxeagle/git-submodule-main.git
   083aae0..07c7f3b  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

<image src="./images/git-submodule-modify.png"/>

## 更新代码
1. 主项目 git pull
```shell
➜  git-submodule-main git:(master) git pull
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 2 (delta 1), reused 2 (delta 1), pack-reused 0
Unpacking objects: 100% (2/2), done.
From https://github.com/hbxeagle/git-submodule-main
   083aae0..07c7f3b  master     -> origin/master
Fetching submodule git-submodule-one
From https://github.com/hbxeagle/git-submodule-one
   a6a2e51..66cd3cc  master     -> origin/master
Updating 083aae0..07c7f3b
Fast-forward
 git-submodule-one | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```
2. 执行 git status 查看是否有新的 submodule commit
```shell
➜  git-submodule-main git:(master) git pull
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 2 (delta 1), reused 2 (delta 1), pack-reused 0
Unpacking objects: 100% (2/2), done.
From https://github.com/hbxeagle/git-submodule-main
   083aae0..07c7f3b  master     -> origin/master
Fetching submodule git-submodule-one
From https://github.com/hbxeagle/git-submodule-one
   a6a2e51..66cd3cc  master     -> origin/master
Updating 083aae0..07c7f3b
Fast-forward
 git-submodule-one | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
➜  git-submodule-main git:(master) ✗ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   git-submodule-one (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
```
3. 执行 git submodule update
```shell
➜  git-submodule-main git:(master) ✗ git submodule update
Submodule path 'git-submodule-one': checked out '66cd3cc9898c0db167af1f275db2270c7ae6b51d'
➜  git-submodule-main git:(master) git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
➜  git-submodule-main git:(master)
```
<image src="./images/git-submodule-pull.png"/>

## merge 子模块冲突

## 移除子模块


