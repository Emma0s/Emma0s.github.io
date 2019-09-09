---
title: Git操作指南  
date: 2019-09-03 14:50:45  
categories: 实习  
comment: true
---
[gitCheatSheet](./images/gitCheatSheet.png)
# 寻常操作
查看此次修改内容：git diff  
查看提交日志：复杂版 ==> git log; 简化版 ==> git log –pretty=oneline

# 版本回退
查找历史版本：git reflog.  
版本回退/前进：git reset –hard 版本ID.  
HEAD:当前版本. HEAD^:上一个版本

# 撤销修改
丢弃工作区(未add)修改：git checkout – file.  
丢弃暂存区(未commit)修改：git reset HEAD file  
丢弃版本库（未push至远程库）修改：版本回退。

# 删除文件/文件恢复
删除文件：git rm file  
文件恢复：git checkout – file(用版本库里的版本替换工作区的版本,注意：从来没有被添加到版本库就被删除的文件，是无法恢复的！)

# 分支管理
查看分支：git branch  
创建+切换分支：git checkout -b name（不加-b纯切换）  
合并某分支到当前分支：git merge name  
删除分支：git branch -d name

## 解决冲突
将git合并失败的文件手动编辑为希望的内容，再提交.  
查看分支合并图：git log –graph –pretty=oneline  

## 分支管理
'fast forward'模式，合并删除分支后，会丢掉分支信息，看不出做过合并:git merge name.  
'–no-ff'模式，merge时会生成新的commit，能看出做过合并:git merge –no-ff -m commit text name

## Bug分支
修复bug ==> 创建bug分支进行修复，然后合并删除该分支  
存储工作现场：git stash  
恢复工作现场：git stash apply（恢复不删除stash）;git stash pop（恢复并删除stash）

## feature分支
开发新feature,最好新建分支  
强行丢弃未合并的分支：git branch -D name

## 团队开发
1.git push origin branch-name 推送自己的修改；  
2.如果推送失败，则远程分支比你的本地更新，用git pull试图合并；  
3.如果合并有冲突，手动解决冲突，并在本地提交；  
4.冲突解决后，git push origin branch-name推送就能成功！  
（注意：如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch –set-upstream-to branch-name origin/branch-name）

## Rebase
- 干净、线性的提交历史，没有不必要的合并提交 ==> git rebase  
- 保存项目完整的历史，避免重写公共分支上的commit ==> git merge  

切到本地分支：git checkout local  
交互式rebase：git rebase -i HEAD~2 //合并两个  
普通rebase：git rebase master –> 解决冲突 –> git rebase –continue  

# 标签管理
新建标签：git tag 'tagname', 默认在HEAD新建，也可指定commit id  
指定标签信息：git tag -a 'tagname' -m 'blablabla...'  
查看所有标签：git tag  
推送本地标签：git push origin 'tagname'  
推送全部未推送过的本地标签：git push origin –tags  
删除本地标签：git tag -d 'tagname'  
删除远程标签：先本地删，后git push origin :refs/tags/'tagname'

# 自定义Git
忽略某些文件：.gitignore
忽略文件的原则是：
- 忽略操作系统自动生成的文件，比如缩略图等；
- 忽略编译生成的中间文件、可执行文件等，比如Java编译产生的.class文件；
- 忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件。

配置命令简写：git config –global alias.co checkout

**仓库Git**配置文件都放在.git/config文件中
**用户Git**配置文件放在用户主目录下的一个隐藏文件.gitconfig中