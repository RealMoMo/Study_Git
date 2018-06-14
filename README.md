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

---------------------

推送数据到远程仓库

git push [remote-name] [branch-name]

---------------------

查看远程仓库信息

git remote show [remote-name]

----------------------

远程仓库的删除和重命名

git remote rename [old_name] [new_name]

git remote rm [remote-name]

================================

打标签

git tag		(显已有的标签)

------------------

新建标签
Git 使用的标签有两种类型：轻量级的（lightweight）和含附注的（annotated）。

---------------------

含附注的标签

git tag -a [tag-name]
例子:
git tag -a v1.0		(Git 会启动vim文本编辑软件供你输入标签说明)

----------------------

显示标签具体信息

git show [tag-name]
例子:
git show v1.0

------------------

签署标签

如果你有自己的私钥，还可以用 GPG 来签署标签，只需要把之前的 -a 改为 -s （译注： 取 signed 的首字母）即可：
$ git tag -s v1.5 -m 'my signed 1.5 tag'
You need a passphrase to unlock the secret key for
user: "Scott Chacon <schacon@gee-mail.com>"
1024-bit DSA key, ID F721C45A, created 2009-02-09

--------------------

轻量级标签
要创建这样的标签，一个 -a，-s 或 -m 选项都不用，直接给出标签名字即可：

例子:
git tag v1.0

----------------------

验证标签

git tag -v [tag-name]

可以使用 git tag -v [tag-name] （译注：取 verify 的首字母）的方式验证已经签署的标签。此命令会调用 GPG 来验证签名，所以你需要有签署者的公钥，存放在 keyring 中，才能验证：

-----------------------

后期加注标签

可以在后期对早先的某次提交加注标签。比如在下面展示的提交历史中：
$ git log --pretty=oneline
omit...
166ae0c4d3f420721acbb115cc33848dfcc2121a started write support
9fceb02d0ae598e95dc970b74767f19372d61af8 updated rakefile
964f16d36dfccde844893cac5b347e7b3d44abbc commit the todo
omit...

我们忘了在提交 “updated rakefile” 后为此项目打上版本号 v1.2，没关系，现在也能做。只要在打标签的时候跟上对应提交对象的校验和（或前几位字符 commit id）即可：

$ git tag -a v1.1 9fceb02

--------------------------

分享标签

默认情况下，git push 并不会把标签传送到远端服务器上，只有通过显式命令才能分享标签到远端仓库。其命令格式如同推送分支，运行 
git push origin [tagname]

推送本地新增的标签，使用--tags

git push origin --tags

===========================

Git命令别名

git config 为命令设置别名

例子:
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status

还可以创造出新的命令
$ git config --global alias.last “log -1 HEAD”

git last  (查看最后一次提交信息)

git config --list or -l (查看当前所有配置)

============================

分支的新建与合并 ![学习链接](Git - 分支的新建与合并  https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E6%96%B0%E5%BB%BA%E4%B8%8E%E5%90%88%E5%B9%B6)

创建分支

git checkout -b [new branch name]   (新建并切换到该分支)
等价于:
git branch [new branch name]		(新建分支)
git checkout [new branch name]		(切换分支)


合并分支

git merge [branch name]


