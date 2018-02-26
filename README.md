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
