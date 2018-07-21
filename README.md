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
 
git diff [+file]    ���������ݴ����Ƚ�   
git diff --cached [+file]  git diff --staged [+file]	�ݴ�����HEAD�Ƚ�
git diff HEAD [+file]    ��������HEAD ( ��ǰ������֧) �Ƚ�
git diff branchName [+file]   ��ǰ��֧���ļ���branchName ��֧���ļ����бȽ�
git diff commitId [+file]     ��ĳһ���ύ���бȽ�

=============================

git commit -a   == git add -A + git commit

============================

git rm +file

==========================

git mv file_from file_to  -> git mv test.txt test1.txt

��ʵ������ git mv ���൱�������������������

$ mv README.txt README
$ git rm README.txt
$ git add README

=================================

�鿴�ύ��ʷ��¼

git log
git log -2 ����ʾ��������θ���
git log -p չ����ʾÿ���ύ�����ݲ���
git log --stat ����ʾ��Ҫ�����ļ�����ͳ��
git --pretty

 git log �г���һЩ�������õ�ѡ������塣
ѡ��			˵��	
-p				��������ʽ��ʾÿ������֮��Ĳ��졣
--word-diff		�� word diff ��ʽ��ʾ���졣
--stat			��ʾÿ�θ��µ��ļ��޸�ͳ����Ϣ��
--shortstat		ֻ��ʾ --stat �����������޸�����Ƴ�ͳ�ơ�
--name-only		�����ύ��Ϣ����ʾ���޸ĵ��ļ��嵥��
--name-status	��ʾ�������޸ġ�ɾ�����ļ��嵥��
--abbrev-commit	����ʾ SHA-1 ��ǰ�����ַ����������е� 40 ���ַ���
--relative-date	ʹ�ý϶̵����ʱ����ʾ�����磬��2 weeks ago������
--graph			��ʾ ASCII ͼ�α�ʾ�ķ�֧�ϲ���ʷ��
--pretty		ʹ��������ʽ��ʾ��ʷ�ύ��Ϣ�����õ�ѡ����� oneline��short��full��fuller �� format�����ָ����ʽ����
--oneline	--pretty=oneline --abbrev-commit �ļ��÷���

git log --since  git log --until
git log --since=2.weeks

��һ������ʵ�õ�git logѡ����·��(path)�����ֻ����ĳЩ�ļ�����Ŀ¼����ʷ�ύ�������� git log ѡ������ָ�����ǵ�·������Ϊ�Ƿ������λ���ϵ�ѡ������������̻��ߣ�--������֮ǰ��ѡ��ͺ����޶���·������(path��Զ�����)


ѡ��				˵��
-(n)				����ʾ����� n ���ύ
--since, --after	����ʾָ��ʱ��֮����ύ��
--until, --before	����ʾָ��ʱ��֮ǰ���ύ��
--author			����ʾָ��������ص��ύ��
--committer			����ʾָ���ύ����ص��ύ��


����һ��ʵ�ʵ����ӣ����Ҫ�鿴 Git �ֿ��У�2008 �� 10 ���ڼ䣬Junio Hamano �ύ�ĵ�δ�ϲ��Ĳ��Խű���λ����Ŀ�� t/ Ŀ¼�µ��ļ���������������Ĳ�ѯ���

$ git log --pretty="%h - %s" --author=gitster --since="2008-10-01" \
   --before="2008-11-01" --no-merges -- t/
   
===================================

��������
   
--amend  (�޸����һ���ύ)

git commit --amend --no-edit	��ǻ��޸��ύ�����޸��ύ��Ϣ
git commit --amend 				��ǻ��޸��ύ������vim�޸��ύ��Ϣ   (�˳�vim��Ҫ�Ȱ� ESC���ٴ� :wq��Enter)


----------------------------------

git reset HARD   +file (ȡ���Ѿ��ݴ���ļ�,Ҳ����ȡ���Ѿ�git add���ļ��ص�not staged)

git checkout -- +file	(ȡ�����ļ����޸Ļص�֮ǰ��״̬,Ҳ�����޸�֮ǰ�İ汾)

===================================

Զ�ֿ̲��ʹ��

git remote  (�����г�ÿ��Զ�̿�ļ������)
����:
$ git remote 
origin

git remote -v  (��ע����Ϊ --verbose �ļ�д��ȡ����ĸ����ʾ��Ӧ�Ŀ�¡��ַ)
����:
$ git remote -v  
origin  https://github.com/RealMoMo/Study_Git.git (fetch)
origin  https://github.com/RealMoMo/Study_Git.git (push)

---------------------

���Զ�ֿ̲�

git remote add [shortname] [url]
����:
$git remote add pb https://github.com/RealMoMo/Practice_Git.git
$ git remote -v
origin  https://github.com/RealMoMo/Study_Git.git (fetch)
origin  https://github.com/RealMoMo/Study_Git.git (push)
pb      https://github.com/RealMoMo/Practice_Git.git (fetch)
pb      https://github.com/RealMoMo/Practice_Git.git (push)
���ַ��� pb ָ����Ӧ�Ĳֿ��ַ�ˡ�

-----------------------

��Զ�ֿ̲�ץȡ����

git fetch [remote-name]

---------------------

�������ݵ�Զ�ֿ̲�

git push [remote-name] [branch-name]

---------------------

�鿴Զ�ֿ̲���Ϣ

git remote show [remote-name]

----------------------

Զ�ֿ̲��ɾ����������

git remote rename [old_name] [new_name]

git remote rm [remote-name]

================================

���ǩ

git tag		(�����еı�ǩ)

------------------

�½���ǩ
Git ʹ�õı�ǩ���������ͣ��������ģ�lightweight���ͺ���ע�ģ�annotated����

---------------------

����ע�ı�ǩ

git tag -a [tag-name]
����:
git tag -a v1.0		(Git ������vim�ı��༭������������ǩ˵��)

----------------------

��ʾ��ǩ������Ϣ

git show [tag-name]
����:
git show v1.0

------------------

ǩ���ǩ

��������Լ���˽Կ���������� GPG ��ǩ���ǩ��ֻ��Ҫ��֮ǰ�� -a ��Ϊ -s ����ע�� ȡ signed ������ĸ�����ɣ�
$ git tag -s v1.5 -m 'my signed 1.5 tag'
You need a passphrase to unlock the secret key for
user: "Scott Chacon <schacon@gee-mail.com>"
1024-bit DSA key, ID F721C45A, created 2009-02-09

--------------------

��������ǩ
Ҫ���������ı�ǩ��һ�� -a��-s �� -m ѡ����ã�ֱ�Ӹ�����ǩ���ּ��ɣ�

����:
git tag v1.0

----------------------

��֤��ǩ

git tag -v [tag-name]

����ʹ�� git tag -v [tag-name] ����ע��ȡ verify ������ĸ���ķ�ʽ��֤�Ѿ�ǩ��ı�ǩ������������ GPG ����֤ǩ������������Ҫ��ǩ���ߵĹ�Կ������� keyring �У�������֤��

-----------------------

���ڼ�ע��ǩ

�����ں��ڶ����ȵ�ĳ���ύ��ע��ǩ������������չʾ���ύ��ʷ�У�
$ git log --pretty=oneline
omit...
166ae0c4d3f420721acbb115cc33848dfcc2121a started write support
9fceb02d0ae598e95dc970b74767f19372d61af8 updated rakefile
964f16d36dfccde844893cac5b347e7b3d44abbc commit the todo
omit...

�����������ύ ��updated rakefile�� ��Ϊ����Ŀ���ϰ汾�� v1.2��û��ϵ������Ҳ������ֻҪ�ڴ��ǩ��ʱ����϶�Ӧ�ύ�����У��ͣ���ǰ��λ�ַ� commit id�����ɣ�

$ git tag -a v1.1 9fceb02

--------------------------

�����ǩ

Ĭ������£�git push ������ѱ�ǩ���͵�Զ�˷������ϣ�ֻ��ͨ����ʽ������ܷ����ǩ��Զ�˲ֿ⡣�������ʽ��ͬ���ͷ�֧������ 
git push origin [tagname]

���ͱ��������ı�ǩ��ʹ��--tags

git push origin --tags

===========================

Git�������

git config Ϊ�������ñ���

����:
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status

�����Դ�����µ�����
$ git config --global alias.last ��log -1 HEAD��

git last  (�鿴���һ���ύ��Ϣ)

git config --list or -l (�鿴��ǰ��������)

============================

��֧���½���ϲ� [ѧϰ����](https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E6%96%B0%E5%BB%BA%E4%B8%8E%E5%90%88%E5%B9%B6)

������֧

git checkout -b [new branch name]   (�½����л����÷�֧)
�ȼ���:
git branch [new branch name]		(�½���֧)
git checkout [new branch name]		(�л���֧)


�ϲ���֧

git merge [branch name]

ɾ����֧

git branch -d [branch name]

==============================

��֧�Ĺ���

�г���ǰ���з�֧���嵥

git branch 
����:
$ git branch
  iss53
* master
  testing
  
-------------------------------  

�鿴������֧���һ���ύ�������Ϣ

git branch -v
$ git branch -v
  iss53   93b412c fix javascript issue
* master  7a98805 Merge branch 'iss53'
  testing 782fd34 add scott to the author list in the readmes

---------------------------------

Ҫ�Ӹ��嵥��ɸѡ�����Ѿ�������δ���뵱ǰ��֧�ϲ��ķ�֧�������� --merged �� --no-merged ѡ�Git 1.5.6 ���ϰ汾���������� git branch --merged �鿴��Щ��֧�ѱ����뵱ǰ��֧����ע��Ҳ����˵��Щ��֧�ǵ�ǰ��֧��ֱ�����Ρ�����

$ git branch --merged
  iss53
* master
֮ǰ�����Ѿ��ϲ��� iss53������������ῴ������һ����˵���б���û�� * �ķ�֧ͨ���������� git branch -d ��ɾ����ԭ��ܼ򵥣���Ȼ�Ѿ��������������Ĺ������ϵ���������֧��ɾ��Ҳ������ʧʲô��

��������� git branch --no-merged �鿴��δ�ϲ��Ĺ�����

$ git branch --no-merged
  testing
  
-------------------------------

������ʾ��δ�ϲ������ķ�֧��������Щ��֧�л���������δ�ϲ������Ĺ����ɹ������Լ򵥵��� git branch -d ɾ���÷�֧����ʾ������Ϊ�������ᶪʧ���ݣ�

$ git branch -d testing
error: The branch 'testing' is not fully merged.
If you are sure you want to delete it, run 'git branch -D testing'.
�����������ȷʵ��Ҫɾ���÷�֧�ϵĸĶ��������ô�д��ɾ��ѡ�� -D ǿ��ִ�У�����������ʾ��Ϣ�и�����������

ǿ��ɾ����֧
git branch -D [branch name]

==============================  

Զ�̷�֧


�鿴����Զ�̷�֧

git branch -a 

--------------------------------

���ͱ��ط�֧

git push [Զ�ֿ̲���] [��֧��]
git push [origin] [��֧��]:[��Զ�̷�֧��]  (�������͵�Զ�̷�֧��)

����:
git push origin remotebranch
or
git push origin remotebranch:dev

---------------------------------

ɾ��Զ�̷�֧

git push [Զ����] :[��֧��]

����:
git push origin :dev

===============================

��֧�ı��[ѧϰ����](https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E5%8F%98%E5%9F%BA)

git rebase

===============================

Git����-�޶��汾ѡ��

��֧����
ָ��һ���ύ����ֱ�ӵķ���Ҫ����һ��ָ�����ķ�֧���á�
�������Ҫ��ʾһ����֧�����һ���ύ�Ķ���������� master ��ָ֧�� ca82a6d����ô����������ǵȼ۵ģ�

git show [last commit id] == git show [branch name]

$ git show ca82a6dff817ec66f44342007202690a93763949
$ git show master


git rev-parse [branch name]

�������֪��ĳ����ָ֧���ĸ��ض��� SHA�������뿴�κ�һ�������б���д�� SHA-1�������ʹ��һ������ rev-parse �� Git ̽�⹤�ߡ�����˵��rev-parse ��Ϊ�˵ײ�����������ճ�������Ƶġ���������ʱ���뿴 Git ���ڵ��״���ʲô״̬ʱ�������ܻ�����á���������Զ���ķ�֧��ִ�� rev-parse��

$ git rev-parse master
ca82a6dff817ec66f44342007202690a93763949

-----------------------------------

������־��ļ��

�鿴������־(һ�ݼ�¼������������ HEAD �ͷ�֧���õ���־��)
git reflog

����:
git reflog
1a95aa1 HEAD@{0}: checkout: moving from remotebranch to master
1a95aa1 HEAD@{1}: checkout: moving from master to remotebranch
1a95aa1 HEAD@{2}: pull origin master: Fast-forward
3eaba28 HEAD@{3}: commit: [feature]add how to manger branch
f00db4f HEAD@{4}: commit: [feature]add simple about branch create and merge
93d3b8e HEAD@{5}: commit (merge): Merge branch 'learn_branch'
f81260b HEAD@{6}: checkout: moving from learn_branch to master

-----------------------------

�������鿴�ֿ��� HEAD ��n��ǰ��ֵ�������ʹ��������־������е� @{n} ���ã�

����:
$ git reflog @{5}
935fded refs/heads/master@{5}: pull origin master: Fast-forward
b774f95 refs/heads/master@{6}: commit: [feature]add git log command using
3f54911 refs/heads/master@{7}: commit: [feature]update git diff command chinese instructions
4a7840f refs/heads/master@{8}: commit: [feature]add git mv command info
0178235 refs/heads/master@{9}: commit: [feature]delete test.txt file using git rm command

------------------------

�鿴�ض�������־
git show HEAD@{n}

����:
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

��Ҫ�������� git log �����ʽ��������־��Ϣ����������� 
git log -g

----------------------------

git diff --check
�ύ֮ǰ����ѿ��ܵĶ�����ַ������г���

=============================

git ����

����

git stash
�������ء������Ի�ȡ�㹤��Ŀ¼���м�״̬����Ҳ�������޸Ĺ��ı�׷�ٵ��ļ����ݴ�ı���������������浽һ��δ������Ķ�ջ�У���ʱ��������Ӧ�á�

git stash list
�鿴���еĴ���

git stash apply
����Ӧ������һ��ʵʩ�Ĵ���

git stash apply stash@{2}
ָ��Ӧ�õĴ��أ�ͨ������ָ��������㲻ָ����Git Ĭ��ʹ������Ĵ��ز�����Ӧ����



���ӣ�

1.�鿴��Ŀ״̬
�� git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
  
2.�ݴ�
�� git stash
Saved working directory and index state WIP on master: 7f5395d [feature]add git Revision knowledge
HEAD is now at 7f5395d [feature]add git Revision knowledge
  
3.�ٲ鿴��Ŀ״̬
�� git status
On branch master
nothing to commit, working tree clean

4.�鿴���еĴ���
�� git stash list
stash@{0}: WIP on master: 7f5395d [feature]add git Revision knowledge
stash@{1}: WIP on master: 7f5395d [feature]add git Revision knowledge
stash@{2}: WIP on master: 7f5395d [feature]add git Revision knowledge

5.�ָ�
�� git stash apply
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")



