> 				本笔记适合已有一些 Git 基础的人来学习！  所有命令均可在 [Git文档官网](https://git-scm.com/book/zh/v2) 查询学习 

### 1.1、配置 Git

#### 1.1.1、配置 user 信息

```bash
$ git config --global user.name 'yeshuai'
$ git config --global user.email 'yeshuai0329@aliyun.com'
```

#### 1.1.2、config 的三个作用域

- 缺少等同于local

```bash
$ git config --local  // local只对某个git仓库有效
$ git config --global  // global 对当前用户所有git仓库有效
$ git config --system  // system 对系统所有登录的用户有效
```

#### 1.1.3、显示 config 的配置信息，加 --list

```bash
$ git config --local --list // local只对某个git仓库有效
$ git config --global --list // global 对当前用户所有git仓库有效
$ git config --system  --list// system 对系统所有登录的用户有效
```



### 1.2、创建 Git 仓库

#### 1.2.1、 两种场景

**1.	把已有的项目纳入Git管理**

```bash
$ cd xxx  // xxx 是项目代码所在文件夹
$ git init // 初始化 git 仓库，会生成.git文件夹。
```

**2.	新建的项目直接用 Git 管理**

```bash
$ cd xxx  // xxx 是某个文件夹
$ git init your_project // 初始化 git 仓库 ,并且在该目录下创建和项目名称同名(your_project)的文件夹
$ cd your_project
```

### 1.3 Git 工作流程

Git 仓库： 工作区 ----------> 暂存区 -----------> 版本历史区 ------------> 远端

- 工作区、暂存区、历史区 都是在计算机本地。远端是在互联网云端
- 在计算机本地修改代码的地方叫工作区，工作区的代码是未被追踪的。
- 通过 `git add xxx(文件,如果是所有文件可以用 . 表示)`  可以把工作区修改的代码,提交到暂存区。
- 通过 `git commit -m '提交信息'` 命令，可以把暂存区代码提交到版本历史区。
- 通过 `git push` 命令可以把已经提交的提示版本提交到远端



### 1.4 Git 的命令

#### 1.4.1、创建本地仓库，会生成 .git 文件夹

```bash
$ git init
```

#### 1.4.2、将本地仓库的数据传输到暂存区

```bash
$ git add . (.提交所有改动的文件到暂存区)
$ git add style/long.css (提交style/long.css文件到暂存区)
```

#### 1.4.3、查询工作区和暂存区数据工作状态

```bash
$ git status
```

#### 1.4.4、将暂存区的改动提交到版本历史区

```bash
$ git commit -m 'xxxxx'   // xxxxx是对本次暂存区到版本历史区的改动描述
$ git commit -am 'xxxxx'   // 直接将工作区的改动提交到版本历史区
```

#### 1.4.5、修改版本历史commit 的 message

```bash
 git commit --amend // 修改最近一次 commit message // 写完以后w是写进去q是退出
```

#### 1.4.6、展示版本历史区的历史纪录

```bash
$ git log  // 会展示最近几次暂存区到版本历史区的改动
$ git log --oneline  // 会展示最近几次暂存区到版本历史区的改动(区别是每次改动是以一行的形式展示，展示数量多于git log)
$ git log -n4 --oneline // 简介的展示最近四条commit数据
```

#### 1.4.7、查看/创建/切换/删除分支

```bash
$ git barnch // 查看本地存在的分支
$ git barnch -a // 查看本地和远端所有的存在的分支
$ git barnch -r // 看远端所有的存在的分支
$ git barnch -av // 查看本地和远端所有的存在的分支,带commit记录
$ git barnch -rv // 查看本地和远端所有的存在的分支,带commit记录
$ git checkout fix/delname  // 创建一个fix/delname分支
$ git branch fix/delname  // 切换到fix/delname分支
$ git checkout -d fix/delname // 创建一个fix/delname分支，并且切换到fix/delname分支
$ git branch -D fix/delname  // 删除fix/delname分支
$ git branch -m fix/delname  fix/editname // 修改fix/delname分支,为fix/editname,远程也会被修改
```

#### 1.4.8、克隆仓库

```bash
$ git clone xxx (xxx是指的传输协议的地址，一般常用http 和 ssh)
```

#### 1.4.9、关联本地仓库和远端仓库

```bash
1. 查看是否连接成功
$ git remote -v
2. 添加关联地址
$ git remote add aaa bbb  // aaa 是给添加的地址的名字 ， bbb 是添加的地址
3. 删除关联的地址
$ git remote remove aaa  // aaa 是要删除的远端地址的名字
4. 第一次推送本地仓库到GitHub
$ git push -u origin main 
5. 以后推送本地仓库代码到main分支
$ git push
```

#### 1.4.10、从远端拉区代码

```bash
$ git fetch
$ git pull
// git fetch 从远端拉去最新代码回来以后不会自动合并，git pull 拉去代码回来以后会进行 merge 合并
```



### 1.5 Git 使用过程中遇到的问题

#### 1.5.1、工作区和暂存区怎么比较文件差异

``` bash
$ git diff  // 默认比较工作区和暂存区的文件差异
```

#### 1.5.2、暂存区和HEAD指针怎么比较文件差异

```bash
$ git diff --cached  // 必须添加 --cached
```

#### 1.5.3、暂存区怎么恢复成HEAD指针一样的

```bash
$ git reset HEAD // 回复暂存区的文件和HEAD一致
```

#### 1.5.4、工作区怎么恢复成暂存区一样的

```bash
$ git checkout
```

#### 1.5.5、怎么修改最新的commit的message

```bash
$ git commit --amend // 修改最近一次 commit message // 写完以后w是写进去q是退出
```

#### 1.5.6、怎么消除最后几次的提交/版本的回退

```bash
$ git reset --hard HEAD^ // commit指针回退到上一次的commit状态
$ git reset --hard xxxxx // commit指针回退到xxxx的commit状态(xxxx 是commit哈希值)
```

#### 1.5.7、删除文件

```bash
$ git rm xxx  // 删除文件(xxx是被删除的文件)
```

#### 1.5.8、开发中临时加塞紧急任务

描述： 项目开发过程中，测试让紧急修复一些bug，但是当前分支工作区已经有了一些改动，那么我们就可以先把工作区的改动添加到暂存区。添加到暂存区以后使用`git stash`隐藏现在的改动，然后去修改bug，改完会后回来再使用 `git stash pop` 取出隐藏的改动

```bash
$ git stash  // 隐藏暂存区的改动
$ git stash  pop // 取出暂存区的改动
$ git stash  apply // 取出暂存区的改动
// （pop 和 apply）的区别是: git stash 相当于把暂存区的改动压入到一个stash栈内， 
git stash pop 是取出栈内的改动，同时stash栈内的改动就被移除了。但是apply是取
出站内的改动，但是站内依然存在改动，可以来重复使用。
$ git stash list // 可以查看 stash 栈内的改动
```

#### 1.5.9、合并代码解决冲突

1. **不同人修改了不同的文件**

   > 				当不同的开发人员修改了同一个分支的不同的文件，在git push的时候先git pull 一下代码，git 会很智能的帮我们解决合并问题。

2. **不同的人修改了相同的文件**

   > 				当不同的开发人员修改了同一个分支的相同的文件，在git push的时候先git pull 一下代码，git 会很智能的帮我们解决合并问题。

3. **不同的人修改了相同文件的相同区域的时候**

   > 				当不同的开发人员修改了同一个分支的相同文件的相同区域的时候，在git push的时候先git pull 一下代码，但是此时git 不能够解决这种冲突，要开发人员手动解决冲突。选择当前本地的还是远端的。解决冲突以后，`git commit -m ''`  `git push`。4

4. **不同的人，一个变更了文件名一个变更文件内容**

   > 				当一个开发人员修改了index.html为index.htm,push到远端， 另一个开发人员修改了index.html里面的内容，也push到远端，就会push不上去，因为本地不是最新的代码，要git pull 一下，git 会很智能的帮我们解决这类合并问题。这个跟git 存储文件，监控机制有关系。

5. **不同的人同时修改了文件名**

   > 				当以个开发人员修改了 index.html为index1.html，并推送到了远端，另一个开发人员修改了index.html 为index2.html，并git push。因为本地不是最新的代码，要git pull 一下，此时会有git 冲突，git并不会为我们解决，需要两个开发人员一起讨论研究 具体如何修改代码。

#### 1.5.10、禁止向远端继承分支执行 push -f

```bash
$ git push -f  //禁止向远端继承分支执行 push -f, 此命令一执行，远端代码所有commit记录便会消失
```

### 1.5.11、深聊git push
-  `git push` 默认情况下向远程推送本地所有新添加的 `commit` 记录到远端主机
- `git push` 的完整语法
```javascript
$ git push -f <remotename> <commit SHA>:<remotebranchname>
```
- `<remotename>` 远程仓库名，默认为origin,是在使用`git remote add <remotename> <remoteaddress>`连接本地和远程仓库的时候起的名字,自己定义的默认是origin
- <commit SHA> 提交的唯一码: `commit` 后生成的哈希值
- <remotebranchname> 远程分支名:要推送的分支名

!!! 注意: `git push -f`, 会清除远端主机所有的commit记录,`git push -f origin ac34f232e: master`, 会使origin远端主机仓库的master分支commit记录回退到ac34f232e.  慎用,禁止使用.
#### 1.5.12、分支合并
-  github gitlab 遵循fastfoward原则
-  git merge 合并,是将一个分支合并到当前分支,解决冲突以后会生成一个新的commit记录
-  git rebase 是变基操作,可以达到合并分支效果,是将一个分支合并到当前分支,解决冲突以后会生成一个新的commit记录

#### 1.5.12、配置ssh

1. `cd ~/.ssh` 检查是否电脑又ssh
2. `ssh-keygen -t rsa -C 'github邮箱地址'`
3. 三次回车
4. 根据提示到C盘找pub后缀文件，去vscode复制内容
5. 打开github 点击头像找setting
6. 找ssh ，复制进去。