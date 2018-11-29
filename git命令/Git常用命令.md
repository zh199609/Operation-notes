##### Git常用命令

1.创建仓库 `git init` 将项目装简称git仓库
2.将项目添加到版本库 `git add -A`
3.查看文件状态 `git status`
4.查看文件的修改 `git diff`
5.提交修改文件到仓库 `git commit -a -m '提交描述'`
6.查看提交记录 `git log`
7.git branch -a   查看本地&远程所有的分支
8.git branch -d <branchName>删除本地分支
9.git push origin --delete <BranchName>删除远程分支
10.git branch <branchName>新建分支

##### 撤销

---撤销---
git log  可以查看提交的id

###### --某个文件的撤销--

git log fileName      得到要回滚版本的hash值
git checkout hash值前六位  fileName
git commit -m 'message'
git push
---------完成某个文件的撤销------------

某个文件回滚
git log fileName
git reset hash值  fileName
git commit -m 'revert'
git checkout fileName
git push 



git reset --hard HEAD  撤销工作目录中所有未提交文件的修改内容

Git提供了 `git checkout -- filename` 命令,可以撤销对文件的修改到当前最新版本.同样的,用 `git reset HEAD filename` 也可以将修改的文件回退到最新的版本

**情况2:文件作出修改  已进行add操作 但是没有 commit   想要删除add**

git reset HEAD     撤销全部已提交修改

git reset HEAD filename    撤销对指定文件的修改

**情况四:文件作出修改已push到仓库**   

此次操作之前和之后的commit和history都会保留，并且把这次撤销作为一次最新的提交 
git revert HEAD  撤销前一次 commit 
git revert HEAD^  撤销前前一次 commit 
git revert commit-id  (撤销指定的版本，撤销也会作为一次提交进行保存） 
git revert是提交一个新的版本，将需要revert的版本的内容再反向修改回去，版本会递增，不影响之前提交的内容。

也可以使用reset 



##### 将多次commit合并成一次

git rebase  -i HEAD~最近几次提交次数 | 想要合并的hash值

<img src="QQ截图20181129141923.jpg">







