<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [1. 初始化仓库](#1-初始化仓库)
- [2.与远程仓库建立连接](#2与远程仓库建立连接)
- [3.各种撤回](#3各种撤回)
- [4.分支管理](#4分支管理)
- [5.bug分支](#5bug分支)

<!-- /TOC -->

---------------------------------

# 1. 初始化仓库
- git init  

# 2.与远程仓库建立连接
- git remote add origin https://github.com/minghuan2046/note.git   
    其中origin是远程别称，url是远程仓库地址
- git push -u origin master
    将本地分支推向远程master分支，并且与远程master分支建立关联

# 3.各种撤回  
- ## 撤回工作区的修改  
  git checkout -- xxx     
  这里有两种可能:  
  - 暂存库中没有该文件记录，则文件退回到与版本库中一致  
  - 暂存库中有该文件的记录，则工作区中的记录与暂存区中记录一致

- ## 撤回暂存区的修改
  git reset HEAD readme.md   
  HEAD表示最新版本，上述语句表示将暂存区的修改退回到上一版本，此时工作区还未被回退。
- ## 放弃本地所做的修改，与远程仓库保持一致
  一. 通过git reflog 查询得到远程仓库最后提交的版本号，通过执行
    git reset --hard ××× 回退  
  二. 通过回到之前的版本再git pull

- ## 退回到之前的某一版本
   - 退回一个版本： git reset --hard HEAD^
   - 退回多个版本： git reset --hard ×××  
   注意--与hard之间不能有空格

- ## 查看git日志
  - git log  
  查看每次提交的日志
  - git reflog
  查看所有活动日志

# 4.分支管理
- ## 创建并切换分支  
  git checkout -b dev
  新建dev分支并切换到dev

- ## 切换分支
  git branch dev  

- ## 合并分支
  git merge dev

- ## 删除分支  
  git branch -d dev

# 5.bug分支
- git stash  
  保存工作现场(工作区)
- git stash list  
  列举工作现场
- git stash pop  
  恢复现场
- git stash apply stash@{0}
  恢复到指定现场
- git stash drop stash@{0}
  删除指定现场，其中通过git stash pop恢复的被被自动删除，通过git stash apply恢复的需要手动删除
