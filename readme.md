# Git command

版本库又名仓库(**repository**)
Git Bash

## 仓库初始化
cd <your_repository>
git init

## 列出隐藏文件
ls -ah

## 把文件添加到仓库
git add <yourfile>

## 把文件提交到仓库
git commit -m "wrote a readme file"
> -m 后面输入的是本次提交的说明
> 1 file changed: 1个文件被改动
> 3 insertions: 插入了3行内容

why two steps? add + commit
> 因为*commit*可以一次提交很多文件，所以可以多次*add*不同的文件

