git init

git remote add origin https://github.com/RealMoMo/Study_Git.git  
git pull origin master
git push origin master

git add
git commit -m"your commit info"
git status
git push

  
git diff [+file]    ���������ݴ����Ƚ�   
git diff --cached [+file]  git diff --staged [+file]	�ݴ�����HEAD�Ƚ�
git diff HEAD [+file]    ��������HEAD ( ��ǰ������֧) �Ƚ�
git diff branchName [+file]   ��ǰ��֧���ļ���branchName ��֧���ļ����бȽ�
git diff commitId [+file]     ��ĳһ���ύ���бȽ�


git commit -a   == git add -A + git commit

git rm +file


git mv file_from file_to  -> git mv test.txt test1.txt

��ʵ������ git mv ���൱�������������������

$ mv README.txt README
$ git rm README.txt
$ git add README


test `  adfagagadfdadad 