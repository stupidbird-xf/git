# git 常用命令
- - - - - - - - - 
1. 主分支
   > git clone git地址 从服务器上将代码拉下来

   > git pull 拉取代码

   > git status 查看当前状态

   > git checkout — 文件名 取消当前在工作区的修改

   > git add -A 新增全部文件

   > git diff 版本对比

   > q 退出查看

   > git commit -am”描述” 提交加注释

   > git push 推送

   > git log 查看commit 日志

   > git reset —hard commit _id 回退到某个commit

   > git reset —hard head^ 回退到上一个版本

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

5. 修改git拉取时的http或者ssh
   
   > ls -la

   > cd .git

   > vim config 进入编辑模式

   > i 编辑 url

   > esc :wq 退出编辑模式

6. 修改 host 
   
   > sudo vi /etc/hosts
   
