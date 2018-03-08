## 初始化并提交
```
    git init
    git add README.md
    git commit -m "first commit"
```
## 撤销工作区的修改(版本库（暂存区）和（分支）)
```
    //用暂存区全部或指定的文件替换工作区的文件,这个操作很危险，会清除工作区中未添加到暂存区的改动
    git checkout -- filename
    git checkout .
    //暂存区的目录树会被重写，被 master 分支指向的目录树所替换
    git reset HEAD
    //会直接从暂存区删除文件
    git rm –-cached
```
## 撤销暂存区的修改
```
    //会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件
    git checkout HEAD .
    git reset HEAD -- filename
```
## 比较不同
```
   //比较版本库与工作区的不同
   // git diff HEAD -- readme.txt
   // 工作区与暂存区的比较
   git diff filename
   //工作区与HEAD比较
   git diff HEAD filename
  //!暂存区与HEAD比较 error
  //git diff --stage filename 
  //当前分支与另一分支比较
  git diff branchname filename
  // 与某一次提交比较
  git diff commitId filename
```
## 添加到远程版本库
```
    git remote add origin https://github.com/wblong/test1.git
    git push -u origin master
 ```
## 重新修改一次提交commit
```
    git add .
    git commit --amend --no-edit
    git push origin master --force
```
## 回退到指定版本
```
    //查看执行过的命令
     git reflog master
     //回退到任意版本
     git reset --hard dd9a9fc
```
## 远程先开好分支然后拉到本地
```
    git checkout -b feature-branch origin/feature-branch    //检出远程的feature-branch分支到本地
```
## 本地先开好分支然后推送到远程
```
    git checkout -b feature-branch    //创建并切换到分支feature-branch  
    git push origin feature-branch:feature-branch //推送本地的feature-branch(冒号前面的)分支到远程origin的feature-branch
```
## 查看远程分支
```
    git branch -r
```
## 拉取远程分支并创建本地分支
```
    //方式一
    git checkout -b 本地分支名x origin/远程分支名x
    //方式二
    git fetch origin 远程分支名x:本地分支名x
    git checkout 分支名x
```
## 合并两个提交

```
  //查看提交历史
  git log
  //合并936bf0d之前的提交
  git rebase -i 936bf0d
  //或者,从当前向后数两个版本
  git rebase -i HEAD~2
  //在弹出的编辑窗口中修改pick为s,第一个无须修改
  pick 3ca6ec3   '注释**********'
  s    1b40566   '注释*********'
  //放弃合并
  git rebase --abort
  //如果出现冲突后
  git add .
  git rebase --continue

```
## 新建分支与合并分支
```
    //新建分支iss53,并切换到iss53
    git checkout -b iss53
    //一下两条命令等同于上面一条
    git branch iss53
    git checkout iss53
    git commit -a -m "iss53 is going..."
    //解决主分支上的紧急问题
    git checkout master
    git checkout -b hotfix
    git commit -a -m 'hotfix is solved'
    //切换到主分支，并将hotfix合并到主分支上,删除hotfix分支
    git checkout master
    git merge hotfix
    git branch -d hotfix
    //切换到iss53分支
    git checkout iss53
    git commit -a -m 'finished the new footer [issue 53]'
    //合并#53到master分支
    git checkout master
    git merge iss53
    //分支已经合并到主分支，删除原分支
    git branch -d iss53
```
## 克隆远程版本库的某一分支
```
    git clone -b <branch name> [remote repository address]
```