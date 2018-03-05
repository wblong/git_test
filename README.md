## 重新修改一次提交commit
```
    git add .
    git commit --amend --no-edit
    git push origin master --force
```
## 回退到指定版本
```
     git reflog master
     git reset --hard dd9a9fc
```
## 远程先开好分支然后拉到本地
    git checkout -b feature-branch origin/feature-branch    //检出远程的feature-branch分支到本地
## 本地先开好分支然后推送到远程
    git checkout -b feature-branch    //创建并切换到分支feature-branch  
    git push origin feature-branch:feature-branch    //推送本地的feature-branch(冒号前面的)分支到远程origin的feature-branch(冒号后面的)分支(没有会自动创建)
