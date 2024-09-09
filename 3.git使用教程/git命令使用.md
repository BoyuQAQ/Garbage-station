# git命令

## [视频传送门](https://www.bilibili.com/video/BV1pX4y1S7Dq/?spm_id_from=333.788.top_right_bar_window_history.content.click&vd_source=64709a8217a1bbd540960dd246f1356a)



## [CSDN`git`命令大全传送门](https://blog.csdn.net/weixin_49851451/article/details/123944431?ops_request_misc=%7B%22request%5Fid%22%3A%22EBCDABFB-45C6-46D7-858B-3A5409B7E9F5%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=EBCDABFB-45C6-46D7-858B-3A5409B7E9F5&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-123944431-null-null.142^v100^pc_search_result_base5&utm_term=git 命令&spm=1018.2226.3001.4187)

## 1.当打开git bash的时候要进行鼠标右击打开

## 将git配置环境变量的过程[CSDN](https://blog.csdn.net/wuwang0/article/details/84104388?ops_request_misc=&request_id=&biz_id=102&utm_term=如何运用cmd实现git&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-3-84104388.142^v100^pc_search_result_base5&spm=1018.2226.3001.4187)

### 基础配置

当第一次使用git的时候，需要对自己的身份进行一个说明，可以用如下两个命令去配置自己的名字和自己的邮箱(和登录是有一定区别的只是一个说明性的，想填什么就填什么)：

$ git config –global user.name “laowang”

$ git config --global user.email “laowang@example.com”	

### 创建仓库

如果在本地有项目或者自己在本地像新建一个项目，可以在项目文件夹里边输入

`git init`

#### 克隆项目

克隆github上的某一个项目就从[github](https://github.com/BoyuQAQ?tab=repositories),然后选择人他们的URL ,然后用本地的`git clone`这个命令来去克隆网络上的一个项目

#### 修改文件和创建版本

 当我们创建完仓库后，我们会赋予这个仓库每一个文件都有一个状态，如果是自己新建的仓库的话，那么这个仓库里所有文件都是未被跟踪的，当生成一个版本之后这个未被跟踪的文件，就不会在这个版本里那么他之间的状态或者他之前在哪里修改就无从谈起了

#### 跟踪一个文件

单独的跟踪一个文件或者跟踪一个目录可以用`$ git add <name>`将其变成暂存状态

一般来说一个文件如果被跟踪，那他这辈子在这个仓库里都是被跟踪的，如果想让他不被跟踪的话可以用`$ git rm <name>`来删掉或者也可以加一个`$ git rm --cache <name>`

#### 对跟踪的文件进行修改

可以通过` $ git add <file-name>`来把它的状态设置成缓存状态

` $ git reset HEAD <name>`来取消它的缓存状态

#### 提交

` $ git commit`用来提交修改

`$ git reset head~ --soft`来取消此次提交的修改，但是不能撤销第一次提交

#### 查看文件状态

`git status`

如果想查看更加细致的东西比如第几行第几个字母，可以用`git diff`来进行查询 

`git log`来查看历史提交（可以通过哈希值来找到本次的提交）

`git log`后边加一个`--pretty`可以美化输出，例如：可以通过`git log --pretty=oneline`把每一次提交的信息都变成一行，或者可以自定义一个格式`git log --pretty=format:"%h - %an,%ar:%s"`	%h:简化哈希	%an:作者名字	%ar:修订日期（距今）	%ad:修订日期	%s:提交说明	



## 2.远程仓库L

`git remote add <name>`：连接远程仓库可以给远程仓库起一个名字，一般远程仓库的名字叫做origin 

可以通过`git remote rename <name> <newname>`更改远程仓库的名字

`git push <name> master分支`
