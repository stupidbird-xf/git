# git 常用命令
- - - - - - - - - 

#### 一 常用 拉取推送命令

1. 主分支

   > git clone git地址 从服务器上将代码拉下来

   > git pull 拉取代码

   > git status 查看当前状态

   > git checkout — 文件名 取消当前在工作区的修改

   > git update-index --assume-unchanged 文件名 取消本地提交

   > git update-index --no-assume-unchanged 文件名 取消忽略

   > git add -A 新增全部文件

   > git diff 版本对比

   > q 退出查看

   > git commit -am”描述” 提交加注释

   > git push 推送

   > git log 查看commit 日志

   > git reflog 查看历史命令

2. 分支
 * 新建分支

   > git branch branch-name

 * 删除分支

   > git branch -r 先查看分支

   > git branch -r -d origin/branch-name

   > git push origin :branch-name

 * 分支拉取推送

   > git clone -b branch-name git地址 直接拉取分支上的代码

   > git pull origin branch-name 拉取分支代码

   > git push origin branch-name 推送代码到分支上

   > git checkout branch-name 切换到branch-name分支上

3. 拉取主分支的代码到分支上

   > git status 查看当前是在那个分支上

   > git checkout master 如果没在主分支，切换到主分支

   > git pull 拉取主分支的代码

   > git checkout branch-name 切换到分支上

   > git merge master 将主分支合并到分支上

   > git push origin branch-name 推送分支

4. 解决冲突

   > git stash push 将文件推到一个临时空间
  
   > git stash pop 将文件从临时空间pop下来

5. commit

   > --mixed 
    意思是：不删除工作空间改动代码，撤销commit，并且撤销git add . 操作
    这个为默认参数,git reset --mixed HEAD^ 和 git reset HEAD^ 效果是一样的。

   > --soft  
    不删除工作空间改动代码，撤销commit，不撤销git add . 

   > --hard
    删除工作空间改动代码，撤销commit，撤销git add . 
    注意完成这个操作后，就恢复到了上一次的commit状态。
   
   * commit 但未 push

   > git reset –hard id 
    完成撤销,同时将代码恢复到前一commit_id 对应的版本 

   > git reset id 
    完成Commit命令的撤销，但是不对代码修改进行撤销，可以直接通过git commit 重新提交对本地代码的修改
   
   > git reset --hard commit_id 回退到某个commit 完成撤销,同时将代码恢复到前一commit_id 对应的版本

   > git reset --hard HEAD^ 回退到上一个版本

   * commit 并 push

   1. git reset –soft commit_id 重置至指定版本的提交 保留当前工作区，以便重新提交

   2. git log确认是否成功撤销

   3. git push origin master –force 强制提交当前版本号，以达到撤销版本号的目的(必须添加参数force进行强制提交，否则会提交失败，并报错 报错原因：本地项目版本号低于远端仓库版本号)

   * 修改commit 注释
   
   > git commit --amend 此时会进入默认vim编辑器，修改注释完毕后保存就好了。

#### 二 终端编辑
1. 修改git拉取时的http或者ssh
   
   > ls -la 产看目录

   > cd .git 进入git文件

   > vim config 进入编辑模式

   > i 编辑 url

   > esc :wq 退出编辑模式

2. 修改 host 
   
   > sudo vi /etc/hosts

#### 三 git 配置 ssh

1. 生成密钥对

   > cd .ssh 进入ssh 文件

   > ls 产看目录

   > ssh-keygen -t rsa -C "your_email@youremail.com"   提示Creates a new ssh key using the provided email # Generating public/private rsa key pair.
   Enter file in which to save the key (/home/you/.ssh/id_rsa):

   > enter

   > 输入密码 再次输入密码

2. 添加公钥到你的远程仓库（github）

   > cat .ssh/id_rsa.pub

   > 登陆你的github帐户。点击你的头像，然后 Settings -> 左栏点击 SSH and GPG keys -> 点击 New SSH key

   > 然后你复制上面的公钥内容，粘贴进“Key”文本域内。 title域，自己随便起个名字。

   > 点击 Add key。

   > ssh -T git@github.com 验证这个key是不是正常工作  提示Hi xxx! You've successfully authenticated, but GitHub does not # provide shell access.

3. 修改git的remote url

   > git remote -v  查看你当前的 remote url

   > git remote set-url origin sshurl  调整你的url。