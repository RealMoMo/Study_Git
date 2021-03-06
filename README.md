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

分支的新建与合并 [学习链接](https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E6%96%B0%E5%BB%BA%E4%B8%8E%E5%90%88%E5%B9%B6)

创建分支

git checkout -b [new branch name]   (新建并切换到该分支)
等价于:
git branch [new branch name]		(新建分支)
git checkout [new branch name]		(切换分支)


合并分支

git merge [branch name]

删除分支

git branch -d [branch name]

==============================

分支的管理

列出当前所有分支的清单

git branch 
例子:
$ git branch
  iss53
* master
  testing
  
-------------------------------  

查看各个分支最后一个提交对象的信息

git branch -v
$ git branch -v
  iss53   93b412c fix javascript issue
* master  7a98805 Merge branch 'iss53'
  testing 782fd34 add scott to the author list in the readmes

---------------------------------

要从该清单中筛选出你已经（或尚未）与当前分支合并的分支，可以用 --merged 和 --no-merged 选项（Git 1.5.6 以上版本）。比如用 git branch --merged 查看哪些分支已被并入当前分支（译注：也就是说哪些分支是当前分支的直接上游。）：

$ git branch --merged
  iss53
* master
之前我们已经合并了 iss53，所以在这里会看到它。一般来说，列表中没有 * 的分支通常都可以用 git branch -d 来删掉。原因很简单，既然已经把它们所包含的工作整合到了其他分支，删掉也不会损失什么。

另外可以用 git branch --no-merged 查看尚未合并的工作：

$ git branch --no-merged
  testing
  
-------------------------------

它会显示还未合并进来的分支。由于这些分支中还包含着尚未合并进来的工作成果，所以简单地用 git branch -d 删除该分支会提示错误，因为那样做会丢失数据：

$ git branch -d testing
error: The branch 'testing' is not fully merged.
If you are sure you want to delete it, run 'git branch -D testing'.
不过，如果你确实想要删除该分支上的改动，可以用大写的删除选项 -D 强制执行，就像上面提示信息中给出的那样。

强制删除分支
git branch -D [branch name]

==============================  

远程分支


查看所有远程分支

git branch -a 

--------------------------------

推送本地分支

git push [远程仓库名] [分支名]
git push [origin] [分支名]:[新远程分支名]  (改名推送到远程分支名)

例子:
git push origin remotebranch
or
git push origin remotebranch:dev

---------------------------------

删除远程分支

git push [远程名] :[分支名]

例子:
git push origin :dev

===============================

分支的变基[学习链接](https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E5%8F%98%E5%9F%BA)

git rebase

===============================

Git工具-修订版本选择

分支引用
指明一次提交的最直接的方法要求有一个指向它的分支引用。
如果你想要显示一个分支的最后一次提交的对象，例如假设 master 分支指向 ca82a6d，那么下面的命令是等价的：

git show [last commit id] == git show [branch name]

$ git show ca82a6dff817ec66f44342007202690a93763949
$ git show master


git rev-parse [branch name]

如果你想知道某个分支指向哪个特定的 SHA，或者想看任何一个例子中被简写的 SHA-1，你可以使用一个叫做 rev-parse 的 Git 探测工具。简单来说，rev-parse 是为了底层操作而不是日常操作设计的。不过，有时你想看 Git 现在到底处于什么状态时，它可能会很有用。这里你可以对你的分支运执行 rev-parse。

$ git rev-parse master
ca82a6dff817ec66f44342007202690a93763949

-----------------------------------

引用日志里的简称

查看引用日志(一份记录最近几个月你的 HEAD 和分支引用的日志。)
git reflog

例子:
git reflog
1a95aa1 HEAD@{0}: checkout: moving from remotebranch to master
1a95aa1 HEAD@{1}: checkout: moving from master to remotebranch
1a95aa1 HEAD@{2}: pull origin master: Fast-forward
3eaba28 HEAD@{3}: commit: [feature]add how to manger branch
f00db4f HEAD@{4}: commit: [feature]add simple about branch create and merge
93d3b8e HEAD@{5}: commit (merge): Merge branch 'learn_branch'
f81260b HEAD@{6}: checkout: moving from learn_branch to master

-----------------------------

如果你想查看仓库中 HEAD 在n次前的值，你可以使用引用日志的输出中的 @{n} 引用：

例子:
$ git reflog @{5}
935fded refs/heads/master@{5}: pull origin master: Fast-forward
b774f95 refs/heads/master@{6}: commit: [feature]add git log command using
3f54911 refs/heads/master@{7}: commit: [feature]update git diff command chinese instructions
4a7840f refs/heads/master@{8}: commit: [feature]add git mv command info
0178235 refs/heads/master@{9}: commit: [feature]delete test.txt file using git rm command

------------------------

查看特定引用日志
git show HEAD@{n}

例子:
git show HEAD@{5}

commit 93d3b8ee762149d859dedc65f8e6e8361578982f
Merge: f81260b 4375bc3
Author: Real Mo <czb166@qq.com>
Date:   Thu Jun 14 20:07:04 2018 +0800

    Merge branch 'learn_branch'
    merge hotfix branch and learnbranch to test1.txt

diff --cc test1.txt
index e26b30c,8a52546..54ce729
--- a/test1.txt
+++ b/test1.txt
@@@ -1,1 -1,4 +1,7 @@@
- add test into branch hotfix
 -add new branch in learnbranch
+
++add test into branch hotfix
++
++add new branch in learnbranch
+
+ finish this problem in branch learnbranch
++

----------------------------

想要看类似于 git log 输出格式的引用日志信息，你可以运行 
git log -g

----------------------------

git diff --check
提交之前，会把可能的多余白字符修正列出来

=============================

git 工具

储藏

git stash
“‘储藏”“可以获取你工作目录的中间状态——也就是你修改过的被追踪的文件和暂存的变更——并将它保存到一个未完结变更的堆栈中，随时可以重新应用。

git stash list
查看现有的储藏

git stash apply
重新应用最新一次实施的储藏

git stash apply stash@{2}
指明应用的储藏，通过名字指定。如果你不指明，Git 默认使用最近的储藏并尝试应用它



例子：

1.查看项目状态
λ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
  
2.暂存
λ git stash
Saved working directory and index state WIP on master: 7f5395d [feature]add git Revision knowledge
HEAD is now at 7f5395d [feature]add git Revision knowledge
  
3.再查看项目状态
λ git status
On branch master
nothing to commit, working tree clean

4.查看现有的储藏
λ git stash list
stash@{0}: WIP on master: 7f5395d [feature]add git Revision knowledge
stash@{1}: WIP on master: 7f5395d [feature]add git Revision knowledge
stash@{2}: WIP on master: 7f5395d [feature]add git Revision knowledge

5.恢复
λ git stash apply
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")



你可以看到 Git 重新修改了你所储藏的那些当时尚未提交的文件。在这个案例里，你尝试应用储藏的工作目录是干净的，并且属于同一分支；但是一个干净的工作目录和应用到相同的分支上并不是应用储藏的必要条件。你可以在其中一个分支上保留一份储藏，随后切换到另外一个分支，再重新应用这些变更。在工作目录里包含已修改和未提交的文件时，你也可以应用储藏——Git 会给出归并冲突如果有任何变更无法干净地被应用。



git stash pop 
重新应用储藏，并同时在git stash list立刻移走


apply选项只尝试应用储藏的工作——储藏的内容仍然在栈上。要移除它，你可以运行 git stash drop，加上你希望移除的储藏的名字。
git stash drop +stash[name]



例子：
λ git stash list
stash@{0}: WIP on master: c15bbc2 [feature]add git stash command using
stash@{1}: WIP on master: 7f5395d [feature]add git Revision knowledge
stash@{2}: WIP on master: 7f5395d [feature]add git Revision knowledge
stash@{3}: WIP on master: 7f5395d [feature]add git Revision knowledge


λ git stash drop stash@{1}
Dropped stash@{1} (3fcbf43f5288dfcf98c7dbb141d3399c6a4a857d)


λ git stash list
stash@{0}: WIP on master: c15bbc2 [feature]add git stash command using
stash@{1}: WIP on master: 7f5395d [feature]add git Revision knowledge
stash@{2}: WIP on master: 7f5395d [feature]add git Revision knowledge

-----------------

取消储藏(realmo 不太理解实际例子)

在某些情况下，你可能想应用储藏的修改，在进行了一些其他的修改后，又要取消之前所应用储藏的修改。Git没有提供类似于 stash unapply 的命令，但是可以通过取消该储藏的补丁达到同样的效果：

$ git stash show -p stash@{0} | git apply -R
同样的，如果你沒有指定具体的某个储藏，Git 会选择最近的储藏：

$ git stash show -p | git apply -R
你可能会想要新建一个別名，在你的 Git 里增加一个 stash-unapply 命令，这样更有效率。例如：

$ git config --global alias.stash-unapply '!git stash show -p | git apply -R'
$ git stash apply
$ #... work work work
$ git stash-unapply

--------------------

从储藏中创建分支

git stash branch
如果你储藏了一些工作，暂时不去理会，然后继续在你储藏工作的分支上工作，你在重新应用工作时可能会碰到一些问题。如果尝试应用的变更是针对一个你那之后修改过的文件，你会碰到一个归并冲突并且必须去化解它。如果你想用更方便的方法来重新检验你储藏的变更，你可以运行 git stash branch，这会创建一个新的分支，检出你储藏工作时的所处的提交，重新应用你的工作，如果成功，将会丢弃储藏。

$ git stash branch testchanges
Switched to a new branch "testchanges"
# On branch testchanges
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#      modified:   index.html
#
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#
#      modified:   lib/simplegit.rb
#
Dropped refs/stash@{0} (f0dfc4d5dc332d1cee34a634182e168c4efc3359)
这是一个很棒的捷径来恢复储藏的工作然后在新的分支上继续当时的工作。

=========================

重写历史(此节具体例子复杂，具体看git book)

改变最新一次提交
git commit --amend

-------------------------

修改多个提交说明

例如，你想修改最近三次的提交说明，或者其中任意一次，你必须给git rebase -i提供一个参数，指明你想要修改的提交的父提交，例如HEAD~2或者HEAD~3。可能记住~3更加容易，因为你想修改最近三次提交；但是请记住你事实上所指的是四次提交之前，即你想修改的提交的父提交。

$ git rebase -i HEAD~3

--------------------------

重排提交

--------------------------

拆分提交

===========================

使用Git调试

文件标注
git blame +[file name]

Git会分析你在标注的文件然后尝试找出其中代码片段的原始出处，如果它是从其他地方拷贝过来的话。
git blame -C +[file name]
这真的非常有用。通常，你会把你拷贝代码的那次提交作为原始提交，因为这是你在这个文件中第一次接触到那几行。Git可以告诉你编写那些行的原始提交，即便是在另一个文件里。

----------------------------

二分查找

会在你的提交历史中进行二分查找来尽快地确定哪一次提交引入了错误。
git bisect

例子：
例如你刚刚推送了一个代码发布版本到产品环境中，对代码为什么会表现成那样百思不得其解。你回到你的代码中，还好你可以重现那个问题，但是找不到在哪里。你可以对代码执行bisect来寻找。首先你运行git bisect start启动，然后你用git bisect bad来告诉系统当前的提交已经有问题了。然后你必须告诉bisect已知的最后一次正常状态是哪次提交，使用git bisect good [good_commit]：

$ git bisect start
$ git bisect bad
$ git bisect good v1.0
Bisecting: 6 revisions left to test after this
[ecb6e1bc347ccecc5f9350d878ce677feb13d3b2] error handling on repo

假设这里是没有错误的，那么你就通过git bisect good来告诉 Git 然后继续你的旅程：
$ git bisect good
Bisecting: 3 revisions left to test after this
[b047b02ea83310a70fd603dc8cd7a6cd13d15c04] secure this thing

你再次运行测试然后发现这次提交是错误的，因此你通过git bisect bad来告诉Git：

$ git bisect bad
Bisecting: 1 revisions left to test after this
[f71ce38690acf49c1f3c9bea38e09d82a5ce6014] drop exceptions table

当你完成之后，你应该运行
git bisect reset来重设你的HEAD到你开始前的地方，否则你会处于一个诡异的地方：

$ git bisect reset

==============================

子模块&子树合并(看git book)

==============================

自定义Git

客户端基本配置(看git book)

-----------------------------

Git中的着色

设置color.ui为true来打开所有的默认终端着色。
$ git config --global color.ui true

其他的参数还有false和always，false意味着不为输出着色，而always则表明在任何情况下都要着色，即使 Git 命令被重定向到文件或管道。

想要具体到哪些命令输出需要被着色以及怎样着色或者 Git 的版本很老，你就要用到和具体命令有关的颜色配置选项，它们都能被置为true、false或always：
color.branch
color.diff
color.interactive
color.status

除此之外，以上每个选项都有子选项，可以被用来覆盖其父设置，以达到为输出的各个部分着色的目的。例如，让diff输出的改变信息以粗体、蓝色前景和黑色背景的形式显示：

$ git config --global color.diff.meta "blue black bold"
你能设置的颜色值如：normal、black、red、green、yellow、blue、magenta、cyan、white，正如以上例子设置的粗体属性，想要设置字体属性的话，可以选择如：bold、dim、ul、blink、reverse。

-------------------------------

外部的合并与比较工具

软件: P4Merge

------------------------------

格式化与空白

core.autocrlf
假如你正在Windows上写程序，又或者你正在和其他人合作，他们在Windows上编程，而你却在其他系统上，在这些情况下，你可能会遇到行尾结束符问题。这是因为Windows使用回车和换行两个字符来结束一行，而Mac和Linux只使用换行一个字符。虽然这是小问题，但它会极大地扰乱跨平台协作。

Git可以在你提交时自动地把行结束符CRLF转换成LF，而在签出代码时把LF转换成CRLF。用core.autocrlf来打开此项功能，如果是在Windows系统上，把它设置成true，这样当签出代码时，LF会被转换成CRLF：
$ git config --global core.autocrlf true

Linux或Mac系统使用LF作为行结束符，因此你不想 Git 在签出文件时进行自动的转换；当一个以CRLF为行结束符的文件不小心被引入时你肯定想进行修正，把core.autocrlf设置成input来告诉 Git 在提交时把CRLF转换成LF，签出时不转换：
$ git config --global core.autocrlf input
这样会在Windows系统上的签出文件中保留CRLF，会在Mac和Linux系统上，包括仓库中保留LF。

如果你是Windows程序员，且正在开发仅运行在Windows上的项目，可以设置false取消此功能，把回车符记录在库中：
$ git config --global core.autocrlf false



Git预先设置了一些选项来探测和修正空白问题，其4种主要选项中的2个默认被打开，另2个被关闭，你可以自由地打开或关闭它们。

默认被打开的2个选项是trailing-space和space-before-tab，trailing-space会查找每行结尾的空格，space-before-tab会查找每行开头的制表符前的空格。

默认被关闭的2个选项是indent-with-non-tab和cr-at-eol，indent-with-non-tab会查找8个以上空格（非制表符）开头的行，cr-at-eol让 Git 知道行尾回车符是合法的。

设置core.whitespace，按照你的意图来打开或关闭选项，选项以逗号分割。通过逗号分割的链中去掉选项或在选项前加-来关闭，例如，如果你想要打开除了cr-at-eol之外的所有选项：

$ git config --global core.whitespace \
    trailing-space,space-before-tab,indent-with-non-tab
当你运行git diff命令且为输出着色时，Git 探测到这些问题，因此你也许在提交前能修复它们，当你用git apply打补丁时同样也会从中受益。如果正准备运用的补丁有特别的空白问题，你可以让 Git 发警告：

$ git apply --whitespace=warn <patch>
或者让 Git 在打上补丁前自动修正此问题：

$ git apply --whitespace=fix <patch>
这些选项也能运用于衍合。如果提交了有空白问题的文件但还没推送到上游，你可以运行带有--whitespace=fix选项的rebase来让Git在重写补丁时自动修正它们。

----------------------------

服务器端配置(看git book)

=============================

Git属性(看git book)

有例子如何对word文档进行对比

=============================

Git挂钩&Git强制策略实例(看git book)

=============================

Last Chapter  
GIt内部原理


.git\ 文件夹内容

D:\Documents\GitHub\Study_Git\.git (master)
λ ls
COMMIT_EDITMSG  HEAD       config       hooks/  info/  objects/
FETCH_HEAD      ORIG_HEAD  description  index   logs/  refs/

onfig 文件包含了项目特有的配置选项，info 目录保存了一份不希望在 .gitignore 文件中管理的忽略模式 (ignored patterns) 的全局可执行文件。hooks 目录保存了第七章详细介绍了的客户端或服务端钩子脚本。

另外还有四个重要的文件或目录：HEAD 及 index 文件，objects 及 refs 目录。这些是 Git 的核心部分。objects 目录存储所有数据内容，refs 目录存储指向数据 (分支) 的提交对象的指针，HEAD 文件指向当前分支，index 文件保存了暂存区域信息。


=============================

该章节其余内容(看git book)




