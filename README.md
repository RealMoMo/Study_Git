git init

==============================

git remote add origin https://github.com/RealMoMo/Study_Git.git  
git pull origin master
git push origin master

===============================

git add
git commit -m"your commit info"
git status
git push

===============================
 
git diff [+file]    工作区与暂存区比较   
git diff --cached [+file]  git diff --staged [+file]	暂存区与HEAD比较
git diff HEAD [+file]    工作区与HEAD ( 当前工作分支) 比较
git diff branchName [+file]   当前分支的文件与branchName 分支的文件进行比较
git diff commitId [+file]     与某一次提交进行比较

=============================

git commit -a   == git add -A + git commit

============================

git rm +file

==========================

git mv file_from file_to  -> git mv test.txt test1.txt

其实，运行 git mv 就相当于运行了下面三条命令：

$ mv README.txt README
$ git rm README.txt
$ git add README

=================================

查看提交历史记录

git log
git log -2 仅显示最近的两次更新
git log -p 展开显示每次提交的内容差异
git log --stat 仅显示简要的增改减行数统计
git --pretty

 git log 列出了一些其他常用的选项及其释义。
选项			说明	
-p				按补丁格式显示每个更新之间的差异。
--word-diff		按 word diff 格式显示差异。
--stat			显示每次更新的文件修改统计信息。
--shortstat		只显示 --stat 中最后的行数修改添加移除统计。
--name-only		仅在提交信息后显示已修改的文件清单。
--name-status	显示新增、修改、删除的文件清单。
--abbrev-commit	仅显示 SHA-1 的前几个字符，而非所有的 40 个字符。
--relative-date	使用较短的相对时间显示（比如，“2 weeks ago”）。
--graph			显示 ASCII 图形表示的分支合并历史。
--pretty		使用其他格式显示历史提交信息。可用的选项包括 oneline，short，full，fuller 和 format（后跟指定格式）。
--oneline	--pretty=oneline --abbrev-commit 的简化用法。

git log --since  git log --until
git log --since=2.weeks

另一个真正实用的git log选项是路径(path)，如果只关心某些文件或者目录的历史提交，可以在 git log 选项的最后指定它们的路径。因为是放在最后位置上的选项，所以用两个短划线（--）隔开之前的选项和后面限定的路径名。(path永远放最后)


选项				说明
-(n)				仅显示最近的 n 条提交
--since, --after	仅显示指定时间之后的提交。
--until, --before	仅显示指定时间之前的提交。
--author			仅显示指定作者相关的提交。
--committer			仅显示指定提交者相关的提交。


来看一个实际的例子，如果要查看 Git 仓库中，2008 年 10 月期间，Junio Hamano 提交的但未合并的测试脚本（位于项目的 t/ 目录下的文件），可以用下面的查询命令：

$ git log --pretty="%h - %s" --author=gitster --since="2008-10-01" \
   --before="2008-11-01" --no-merges -- t/
   
===================================

撤销操作
   
--amend  (修改最后一次提交)

git commit --amend --no-edit	标记会修复提交但不修改提交信息
git commit --amend 				标记会修复提交并进入vim修改提交信息   (退出vim需要先按 ESC，再打 :wq，Enter)


----------------------------------

git reset HARD   +file (取消已经暂存的文件,也就是取消已经git add的文件回到not staged)

git checkout -- +file	(取消对文件的修改回到之前的状态,也就是修改之前的版本)

===================================

远程仓库的使用

git remote  (它会列出每个远程库的简短名字)
例子:
$ git remote 
origin

git remote -v  (译注：此为 --verbose 的简写，取首字母，显示对应的克隆地址)
例子:
$ git remote -v  
origin  https://github.com/RealMoMo/Study_Git.git (fetch)
origin  https://github.com/RealMoMo/Study_Git.git (push)

---------------------

添加远程仓库

git remote add [shortname] [url]
例子:
$git remote add pb https://github.com/RealMoMo/Practice_Git.git
$ git remote -v
origin  https://github.com/RealMoMo/Study_Git.git (fetch)
origin  https://github.com/RealMoMo/Study_Git.git (push)
pb      https://github.com/RealMoMo/Practice_Git.git (fetch)
pb      https://github.com/RealMoMo/Practice_Git.git (push)
用字符串 pb 指代对应的仓库地址了。

-----------------------

从远程仓库抓取数据

git fetch [remote-name]

推送数据到远程仓库

git push [remote-name] [branch-name]

查看远程仓库信息

git remote show [remote-name]

远程仓库的删除和重命名

git remote rename [old_name] [new_name]

git remote rm [remote-name]

================================






