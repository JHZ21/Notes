# git:  版本管理



## 编辑config文件

```git
git config --global --edit
```









## ssh 密钥生成

```
ssh-keygen -t rsa -C ‘email’
```



## 全局用户名与邮箱

* 查看

```git
// 查看全局用户名与邮箱
git config --global user.name

git config --global user.email
```

* 清除

```git
git config --global --unset user.name

git config --global --unset user.email
```





## 配置多个Git账户

* [Mac下配置多个Git账户](https://www.jianshu.com/p/6507ce357ad2)





## 提交与还原(工作区 <=> 版本库)

> 工作区—（```git add  <file>```)—> 暂存区—(```git commit -m “ ”```)—> 版本库
>
> 工作区 <—（```git checkout --<file>```)—  暂存区 <—(```git reset HEAD <file>```)— 版本库

| 提交     | 工作区     | =>                                | 暂存区     | =>                          | 版本区     |
| -------- | ---------- | --------------------------------- | ---------- | --------------------------- | ---------- |
|          |            | ```git add  <file>```             |            | ```git commit -m “ ”```     |            |
|          |            |                                   |            |                             |            |
| **回滚** | **工作区** | **<=**                            | **暂存区** | **<=**                      | **版本区** |
|          |            | ```git checkout --<file>```       |            | ```git reset HEAD <file>``` |            |
|          |            | ```git restore --staged <file>``` |            |                             |            |

```
// 缓存所有文件
git add .
git add *
git commit -a  // 缓存并提交
```



## 本地版本库切换

> ```git
> // 恢复为上个版本
> git reset --hard HEAD^  
> git reset --hard HEAD~1
> // 恢复为上上个版本
> git reset --hard HEAD^^ 
> git reset --hard HEAD~2
> 
> git reset --hard 1094a    (1094a : 对应id 的前面一部分)
> // 如果切回过去版本b，git log将消失b未来版本信息，可以通过，翻查命令行，找到未来版本id,还原，或者git reflog查看id
> ```



## 查看日志



### 查看现在版本库状态

```
git log  
git log --pretty=oneline 
```



###  查看历史命令

```
git reflog
```



### 查看分支合并图

```
git log --graph

git log --graph --pretty=oneline --abbrev-commit
```



## rebase

```
// 先不管这个命令
git rebase
```



##  分支用途

- `master`分支是主分支，因此要时刻与远程同步；
- `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。
- 在Git中，分支完全可以在本地自己藏着玩，是否推送，视你的心情而定！



## 分支管理



### 创建分支，切换分支

```
// 创建dev分支，并切换到dev分支c
 git checkout -b dev 
 或
 git switch -c dev
相当于：
 git branch dev   // 创建分支
 git checkout dev // 切换分支
 git switch dev  // 切换分支
 
```



### 查看分支

```
// 查看当前分支:
git branch
```



### 合并分支

```
git merge dev // 合并指定分支到当前分支
```

 #### Fast-forward

> 把本分支( `master` )指向 合并分支（`dev`）的提交
>
> 合并速度非常快
>
> 这种模式下，删除分支后，会丢掉分支信息

#### --no-ff

>merge时生成一个新的commit, 从分支历史上就可以看出分支信息
>
>```
>git merge --no-ff -m "merge with no-ff" dev
>```
>
>无论直接合并与否，分支信息都在保存下来，如何冲突了，修正后提交，分支信息就会出现了



### 删除分支

```
git branch -d dev  // delete 删除dev分支
```

```
// -D：强制删除，未合并，修改为丢失的分支
git branch -D 分支名
```



## 解决merge冲突



### 无分叉

> 如果无分支，任是一条线，可以直接merge, 不会有冲突



### 有分叉

> 如何主线和合并线，有分叉，则需merge后, 手动fix conflict，保存提交, 多余分支也可delete



## * cherry-pick：复制指定提交的改动

> good！

```
git cherry-pick <commit>
eg: git cherry-pick a3d5f13

```

>应用场景如，修改以前代码的bug, master, dev等，都会有该bug,  cherry-pick 可以减少重复劳动
>
> 如果当前工作区，有修改，可以先 stash 隐藏，再cherry-pick 去复制，然后
>stash apply 恢复合并，最后进行冲突修改



## stash 隐藏工作现场

> 无需提交commit，也可以保存改动



### 查看隐藏列表

```git stash list
git stash list
```

```
// 新的在上面，即最新的下标 0
// 所有分支的stash 是放一起的
stash@{0}: WIP on master: 60e5067 merged bug fix 1
stash@{1}: WIP on dev: 5de3141 dev 3
stash@{2}: WIP on dev: 5de3141 dev 3
```



###  隐藏当前工作现场

```
git stash  // 工作区干净了
git stash push -m <message> // 隐藏并输入注释
```



### 恢复工作现场

```
git stash apply 恢复下标0的(最新的)stash 但不删除
git stash pop // 恢复第一个(最新的)stash 并删除
// git stash ( pop | apply ) [-- index] 
git stash apply -- 0  //恢复下标为0的stash
```



### 删除stash

```
// git stash drop [-q|--quiet] [<stash>]
git stash drop 0 // 删除下标0的stash
```





## 远程仓库



### 添加远程库

```
 git remote add origin git@github.com: xxx/learngit.git
```



### 查看远程库信息

```
git remote
> origin
```

```
// 详细信息
git remote -v
> origin  git@github.com:xx/learngit.git (fetch)
> origin  git@github.com:xx/learngit.git (push)  // :说明有push权限
```



### clone:  克隆

```
// 只会克隆 master 分支
git clone git@github.com:xxx/learngit.git
```



### 抓取分支

```
git checkout -b dev origin/dev
```



### 建立连接关系

```
git branch --set-upstream-to=origin/dev dev
```



###  pull:  拉取合并

```
git pull
```

> 与远程库，进行合并，若冲突部分，再进行修改提交
>
> 用于无法直接推送本地库时，进行冲突修正来提交



### push:  推送分支

``` 
git push origin master
git push origin dev
```

* -u

  ```
  git push -u origin master
  ```

  >  -u  ：可以将本地分支和远程的分支关联起来，
  > 简化推送或者拉取的命令



## alias： 别名

### 设置alias

```
 git config --global alias.st status
```

```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

### 删除alias

```git
git config --global --unset alias.st
```

### 编辑config文件

> ​	可以修改alias

```git
git config --global --edit
```

### alias 配置

```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

* config 文件

```
   lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
        st = status
        aa = add .
        ps = push
        pl = pull
        br = branch -v
        co = checkout
```

