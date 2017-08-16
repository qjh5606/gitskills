## 本地操作
### 初始化一个Git仓库
	git init 

### 添加文件到Git仓库
	1.	git add <file>
	2.	git commit	-m "注释,被认为是非常重要的一个环节"

### 查看仓库当前的状态
	git status

### 查看仓库修改内容
	git diff
	
### 回退版本	
	查看仓库历史记录
	git log
	git log --pretty=oneline

	HEAD表示当前版本
	git reset --hard HEAD^	//回退到上一个版本
	
	指定到某个版本:
	git reset --hard <commit id>
	
	确定未来的哪个版本:
	git reflog

### 工作区(仓库目录)/暂存区(stage)

###	Git管理的是修改
	git commit只负责把暂存区的修改提交
	
### 撤销修改:
	在工作区的修改全部撤销
	git checkout -- <file>
	情况1.	在工作区的修改全部撤销,撤销修改就回到和版本库一模一样的状态.
	情况2.	加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态
	
### 删除文件:
	在文件管理区中删除文件的命令行:	rm test.txt
	git rm
	git commit

## 远程仓库
    ssh-keygen -t rsa -C "chenjz1993@qq.com"
    id_rsa是私钥
    id_rsa.pub是公钥
    GitHub-->Account settings-->SSH Keys-->Add SSHKey，任意Title，在Key文本框里粘贴id_rsa.pub文件的内容
    
### 添加远程仓库
    git remote add origin git@github.com:qjh5606/learngit.git
    
    远程库的名字就是origin，
	这是Git默认的叫法，也可改成别的
	但origin这个名字一看就知道是远程库
    
### 把本地库的所有内容推送到远程库

    要关联一个远程库，使用命令
    git remote add origin git@server-name:path/repo-name.git；
    
    例如:git remote add origin git@github.com:qjh5606/learngit.git
    

    关联后，第一次推送master分支的所有内容,使用命令
    git push -u origin master
	
    此后每次本地提交后，可以使用命令推送最新修改
    git push origin master 
    
### 从远程仓库克隆

     git clone git@github.com:michaelliao/gitskills.git
     
## 分支管理	 
	 
### 创建分支与合并分支

	查看分支：git branch	//带*号为当前指向分支

	创建分支：git branch <name>

	切换分支：git checkout <name>	

	创建+切换分支：git checkout -b <name>	// 

	合并某分支到当前分支：git merge <name>	// name指的是指定的某分支

	删除分支：git branch -d <name>	// 

### 冲突解决

	分支合并图:	git log --graph
				git log --graph --pretty=oneline --abbrev-commit	
				
### 分支管理策略
	
	在实际开发中，我们应该按照几个基本原则进行分支管理：

	首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

	干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

	你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。
	
	合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，
	而fast forward合并就看不出来曾经做过合并。
	
### Bug分支

	