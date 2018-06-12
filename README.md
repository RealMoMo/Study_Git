git init

git remote add origin https://github.com/RealMoMo/Study_Git.git  
git pull origin master
git push origin master

git add
git commit -m"your commit info"
git status
git push

git diff    
git diff +file
git diff --cached 
git diff --staged


git commit -a   == git add -A + git commit

git rm +file


git mv file_from file_to  -> git mv test.txt test1.txt

其实，运行 git mv 就相当于运行了下面三条命令：

$ mv README.txt README
$ git rm README.txt
$ git add README


test `  adfagagadfdadad 