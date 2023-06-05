







![image-20230604213511604](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230604213511604.png)



Git配置

```shell
$ git config --global user.name "yaron"
$ git config --global user.email "yaron@163.com"
$ git config --global --list
# 查看版本冲突工具
$ git config --global merge.tool vimdiff
```



创建版本库

```shell
# 初始化
$ git init
# 添加文件 
$ git add Test.java
# 提交文件  vim 添加注释后，wq保存后 就提交了
$ git commit Test.java
```



工作区和暂存区

![image-20230604224137229](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230604224137229.png)





```shell

$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ddd.txt
# 简短状态信息        
$ git status -s        

# 提交时添加 注释信息 -m
$ git commit -m commit_info

# 查看修改历史
$ git log abc.txt
commit 2940e3544d00583e8037cc3d864bb1c1681c61d1 (HEAD -> master)
Author: Yaron <yangyu9507@163.com>
Date:   Sun Jun 4 22:59:14 2023 +0800

    updating_again

commit 06b68496a807aa13504f4085be1a3b7d17a0b642
Author: Yaron <yangyu9507@163.com>
Date:   Sun Jun 4 22:55:57 2023 +0800

    update

commit 9293dc9cf9fd0fbb846e75b3b185321f4050c96b
Author: Yaron <yangyu9507@163.com>
Date:   Sun Jun 4 22:26:18 2023 +0800

    first sumbit
    
$ git log --oneline abc.txt
2940e35 (HEAD -> master) updating_again
06b6849 update
9293dc9 first sumbit
    
$ git log --reverse abc.txt
commit 9293dc9cf9fd0fbb846e75b3b185321f4050c96b
Author: Yaron <yangyu9507@163.com>
Date:   Sun Jun 4 22:26:18 2023 +0800

    first sumbit

commit 06b68496a807aa13504f4085be1a3b7d17a0b642
Author: Yaron <yangyu9507@163.com>
Date:   Sun Jun 4 22:55:57 2023 +0800

    update

commit 2940e3544d00583e8037cc3d864bb1c1681c61d1 (HEAD -> master)
Author: Yaron <yangyu9507@163.com>
Date:   Sun Jun 4 22:59:14 2023 +0800

    updating_again

```





```shell
# 差异比较 
$ git diff ccc.txt
diff --git a/ccc.txt b/ccc.txt
index 0013193..b9ec662 100644
--- a/ccc.txt
+++ b/ccc.txt
@@ -1 +1,7 @@
-ddddddccc
\ No newline at end of file
+ddddddccc
+sdfsadf
+
+fasdfsf
+a
+sf
+sd
\ No newline at end of file

# 还原修改
$ revert

# 删除
$ 1. delete              从本地仓库中删除    git rm a.txt
$ 2. delete (keep local) 从本地仓库中删除, 但本地保留
```





```shell
# 重命名
$ git mv d.txt d2.txt

```





```shell
# 连接github 有 https /  ssh 2种方式
1. https 每次都需要密码
2. ssh  非对称加密
   github 持有公钥
   用户    持有私钥
   
# 生成ssh  密钥

$ ssh-keygen -t rsa

Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Administrator/.ssh/id_rsa):
/c/Users/Administrator/.ssh/id_rsa already exists.
Overwrite (y/n)?

id_rsa     私钥
id_rsa.pub 公钥
   
# 在Github上配置公钥
https://github.com/settings/keys
New SSH key

# 将 id_rsa.pub 公钥 的内容添加到 key 中
```

![image-20230604233526867](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230604233526867.png)



```shell
# Push到 github

git@github.com:yangyu9507/gittest.git

# 查看远程库信息
$ git remote -v
origin  git@github.com:yangyu9507/gittest.git (fetch)
origin  git@github.com:yangyu9507/gittest.git (push)

# 本地仓库 关联 远程一个号 origin 仓库
$ git remote add origin git@github.com:yangyu9507/gittest.git

$ git push -u origin master
The authenticity of host 'github.com (20.205.243.166)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
Enumerating objects: 28, done.
Counting objects: 100% (28/28), done.
Delta compression using up to 8 threads
Compressing objects: 100% (21/21), done.
Writing objects: 100% (28/28), 2.21 KiB | 565.00 KiB/s, done.
Total 28 (delta 7), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (7/7), done.
To github.com:yangyu9507/gittest.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.

```



使用TortoiseGit同步到远程仓库

![](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230605000341230.png)

![image-20230604235533934](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230604235533934.png)



```shell


$ git add eee.txt
$ git commit eee.txt -m eee.ttt
[master 8e09d89] eee.ttt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 eee.txt

# 用TortoiseGit 选择 git sync 同步
```

 推送  拉取 都可以

![image-20230605000420759](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230605000420759.png)



从远程创建取代码 

```shell

$ git clone git@github.com:yangyu9507/gittest.git

$ git fetch
 从远程获取最新版本到本地， 不会自动 merge
$ git pull
  从远程获取最新版本到本地，并merge到本地
```

删除远程仓库 在Github 上



# 分支管理 





```shell
# 创建分支
$ git branch dev2
# 删除分支
$ git branch -d dev2
```



# 分支标签

 

```shell
# 查看已有的标签
$ git tag
# 新建标签
$ git tag v1.0
# 新建标签 并添加标签说明 
$ git tag -a v2.0
# 删除标签
$ git tag -d v2.0
Deleted tag 'v2.0' (was 401a181)



```



# Git服务器搭建



```shell

$ yum -y install curl-devel expat-devel gettext-devel openssl-devel zlib-devel perl-devel
$ yum -y install git

$ 创建一个 git用户组和用户，用来运行git服务
$ groupadd git
$ useradd git -g git
# NlWRdPJt7pkEUzXOmKoz
$ passwd git

# 创建证书登录 公钥位于id_rsa.pub文件中，把我们的公钥导入到 /home/git/.ssh/authorized_keys中，一行一个  没有文件 就创建
$ cd /home/git
$ mkdir .ssh
$ chmod 755 .ssh
$ touch .ssh/authorized_keys
$ chmod 644 .ssh/authorized_keys

# 初始化Git仓库
[root@tokyo home]# mkdir gitrepo
[root@tokyo home]# chown git:git gitrepo/
[root@tokyo home]# cd gitrepo/
[root@tokyo gitrepo]# git init --bare yaron.git
Initialized empty Git repository in /home/gitrepo/yaron.git/
# 以上命令创建Git一个空仓库, 服务器上的Git仓库 都以.git结尾, 然后 把仓库所属用户改为git
[root@tokyo gitrepo]# chown -R git:git yaron.git/


```







