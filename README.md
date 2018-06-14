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

��֧���½���ϲ� ![ѧϰ����](Git - ��֧���½���ϲ�  https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E6%96%B0%E5%BB%BA%E4%B8%8E%E5%90%88%E5%B9%B6)

������֧

git checkout -b [new branch name]   (�½����л����÷�֧)
�ȼ���:
git branch [new branch name]		(�½���֧)
git checkout [new branch name]		(�л���֧)


�ϲ���֧

git merge [branch name]


