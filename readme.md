# Git command

[TOC]

版本库又名仓库(**repository**)
Git Bash

## 列出隐藏文件
`$ ls -ah`

## 显示文件内容
`$ cat <yourfile>`

## 仓库初始化
`$ cd <your_repository>`
`$ git init`

## 把文件添加到仓库
`$ git add <yourfile>`

## 把文件提交到仓库
`$ git commit -m "wrote a readme file"`
> `-m` 后面输入的是本次提交的说明
> `1 file changed`: 1个文件被改动
> `3 insertions`: 插入了3行内容

why two steps? `add` + `commit`
> 因为`commit`可以一次提交很多文件，所以可以多次`add`不同的文件

## 查看仓库当前状态
`$ git status`

## 查看仓库文件
`$ git ls-files`

## 查看difference
`$ git diff <yourfile>`



## 查看日志
`$ git log`
`$ git log --pretty=oneline`

## 版本回退
`$ git reset --hard <version>`
`$ git reset --hard HEAD^`
`$ git reset HEAD <file>`
> `HEAD` 指向当前版本 `HEAD^` 指向上一个版本 `HEAD^^` 指向上上个版本 `HEAD~100`

## 查看记录的命令
`$ git reflog`
> 找记录，查看版本号，回退版本

## 工作区和暂存区
工作区(Working Directory) --电脑里能看到的目录，如`Git`文件夹就是一个工作区
版本库(Repository) --工作区有一个隐藏目录`.git`,是Git版本库。其中最重要的是称为**stage**(*index*)的暂存区,还有Git自动为我们自动创建的第一个分支`master`，以及一个指向`master`的一个指针`HEAD`。
![concept1](https://i.loli.net/2021/06/18/BsuzdimyKGStonD.png)

## 管理修改
`Git`跟踪并管理的是修改，而非文件。

## 撤销修改
`$ git restore --worktree <yourfile>`
> 从暂存区恢复工作区(stage->worktree)

`$ git restore -staged <yourfile>`
> 从master恢复暂存区(matser->stage)

`$ git restore --source=HEAD --staged --worktree <file>`
> 从master同时恢复工作区和暂存区

## 删除文件
`$ rm <file>`
`$ git rm <file>` `git add <file>`
`$ git commit`
> 手动删除文件，然后在`master`删除，提交

`$ git restore <file>`
> 手动删除后从版本库里恢复

## 添加远程库
`$ git remote add origin git@github.com:Carrot404/Git.git` origin 远程库的名字

`$ git push -u origin master`
> 把本地库的内容推送到远程 `-u`参数不但会推送给远程，还会将本地和远程分支关联起来

`$ git branch` 查看本地所有分支
`$ git branch -r` 查看远程所有分支
`$ git branch -a` 查看本地和远程所有分支
`$ git branch -d` 删除本地分支
`$ git branch -d -r` 删除远程分支 删除后还要推送到服务器`$ git push origin :<branchname>`

## 删除远程库
`$ git remote rm origin`
> 删除只是结束了本地和远程的绑定关系，并不是物理上删除了远程库。要真正删除远程库，需要登录到GitHub上删除。
`$ git remote -v`

## 从远程库克隆
`$ git clone <ssh>` 本地没有仓库，将远程仓库整个下载过来
`$ git pull origin master` 从远程获取代码并合并本地的版本

![git](https://i.loli.net/2021/06/18/UsAWXofJSbN5xtM.jpg)

## 创建与合并分支

![branch1](https://i.loli.net/2021/06/18/ZmjqQ6b7H1E4clz.png)
![branch2](https://i.loli.net/2021/06/18/WLkSnRa9OPz65Yt.png)

`$ git checkout -b dev` Switch to a new branch 'dev' 相当于以下两条指令
`$ git branch dev`+`$ git checkout dev`
`$ git branch` 查看当前分支

## 解决冲突

当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。
`$ git log --graph` 分支合并图

## 分支管理策略

![strategy](https://i.loli.net/2021/06/18/TAvFZ2BypwrHXdz.png)

`$ git merge --no-ff -m "comment" dev` 普通模式合并，合并后的历史有分支。`fast forward`合并看不出曾经做过合并。

## Bug分支

## Feature分支

## 多人协作

## Rebase
[Git tutorial](https://www.liaoxuefeng.com/wiki/896043488029600)

## 创建标签
`$ git tag v1.0` 打新标签，默认标签打在最新提交的commit
`$ git tag v0.9 <commit id>` 标签打在对应commit id上
`$ git tag` 查看标签
`$ git show <tagname>` 查看标签信息
`$ git tag -a v0.9 -m "version 0.1 released" <commit id>` 创建带有说明的标签

==注意：标签总是和某个commit挂钩。如果这个commit既出现在master分支，又出现在dev分支，那么在这两个分支上都可以看到这个标签。==

## 操作标签

`$ git tag -d v0.9` 删除标签
`$ git push origin <tagname>` 推送标签到远程
`$ git push origin --tag` 一次性推送全部未推送到远程的本地标签
`$ git push origin :refs/tags/v0.9` 先本地删除标签，再删除远程标签

## GitHub
`Repository` 仓库
`Issue` 问题
`Star` 点赞，点赞过的项目会保存在`Star`中
`branch` 仓库的平行版本
`Fork` 拉分支，能复制一个完全相同的项目到账号中
`Pull Request` 提交请求，`Fork`后对其进行修改后，向原作者请求，能成为项目的贡献者。
`Merge` 合并，`Pull Request`审核通过之后将其合并到项目中
`Watch` 观察 `Watch`项目之后，有任何更新，会收到更新通知

## VSCode
`+` = `git add`
`√` = ··`git commit -m "备注信息"`
