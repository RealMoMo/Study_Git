git init

git remote add origin https://github.com/RealMoMo/Study_Git.git  
git pull origin master
git push origin master

git add
git commit -m"your commit info"
git status
git push

  
git diff [+file]    工作区与暂存区比较   
git diff --cached [+file]  git diff --staged [+file]	暂存区与HEAD比较
git diff HEAD [+file]    工作区与HEAD ( 当前工作分支) 比较
git diff branchName [+file]   当前分支的文件与branchName 分支的文件进行比较
git diff commitId [+file]     与某一次提交进行比较


git commit -a   == git add -A + git commit

git rm +file


git mv file_from file_to  -> git mv test.txt test1.txt

其实，运行 git mv 就相当于运行了下面三条命令：

$ mv README.txt README
$ git rm README.txt
$ git add README


test `  adfagagadfdadad 