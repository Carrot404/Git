# Git command

版本库又名仓库(**repository**)
Git Bash

## 列出隐藏文件
ls -ah

## 显示文件内容
cat <yourfile>

## 仓库初始化
cd <your_repository>
git init

## 把文件添加到仓库
git add <yourfile>

## 把文件提交到仓库
git commit -m "wrote a readme file"
> -m 后面输入的是本次提交的说明
> 1 file changed: 1个文件被改动
> 3 insertions: 插入了3行内容

why two steps? add + commit
> 因为*commit*可以一次提交很多文件，所以可以多次*add*不同的文件

## 查看仓库当前状态
git status

## 放弃更改
git restore <yourfile>

## 查看difference
git diff <yourfile>

## 查看日志
git log
git log --pretty=oneline

## 版本回退
git reset --hard <版本号> 
git reset --hard HEAD^
> HEAD 指向当前版本 HEAD^ 指向上一个版本 HEAD^^ 指向上上个版本 HEAD~100

## 查看记录的命令
git reflog
> 找记录，查看版本号，回退版本
