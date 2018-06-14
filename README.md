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

�������ݵ�Զ�ֿ̲�

git push [remote-name] [branch-name]

�鿴Զ�ֿ̲���Ϣ

git remote show [remote-name]

Զ�ֿ̲��ɾ����������

git remote rename [old_name] [new_name]

git remote rm [remote-name]

================================






