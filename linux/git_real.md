## Git Real

### Level 1

### Level 2

#### git diff
查看未stage的改动，包含staged的话可以使用`git dif --staged`。

#### git reset HEAD < file >
移除file的staged状态。

#### git checkout -- < file >
还原file到上次commit的状态。

#### git commit -a -m "Bla Bla Commit"
相当于`git add .`后commit。

#### git reset --soft HEAD^
取消上次commit，但所有changes依然保留在staging里。

#### git commit --amend -m "New Message"
改写上一次commit。

#### git reset --hard HEAD^
取消上次的commit与其包含的所有改变。

#### git reset --hard HEAD^^
取消上两次commit。

#### git remote -v
显示远程的库。

#### git remote add < remote-name (origin) > address
新增一个remote。

#### git push -u < remote-name > < branch-name >
把本地的改动推送到对应的remote和branch。

#### git pull
把remote的内容同步到本地。

#### git remote rm < remote-name >
删除remote。

### Level 3

#### git clone
复制一个库。

#### git branch < branch-name >
创建一个branch。

#### git checkout < branch-name >
切换到 branch。

#### git merge < branch-name >
将branch-name合并到当前branch。

#### git branch -d < branch-name >
删除branch。

#### git checkout -b < branch-name >
相当于`git branch name`加`git checkout name`。

#### Fast-forward与Non-fast-forward
当两条分支都有改动时，不能使用fast-forward。

### Level 4

#### git fetch
将remote的分支的内容同步到本地的对应remote-name上，如origin/master。

#### pull相当于fetch+merge

#### 解决conflict

### Level 5

#### 关于Remote

#### git branch -r
查看所有remote的branch。

#### 关于git pull取得的新分支
git pull取得的remote中新的branch不会立即合并到本地；但可以直接用git checkout来切换到对应branch。

#### git remote show < remote-name >
获得对应remote的信息，包括所有branch。

#### git push origin :< branch-name >
仅删除远端的对应branch，保留本地的。

#### git remote prune < remote-name >
本地上清除已经在remote上上出的branch。

#### Heroku的例子，push时把branch-a推到branch-b上
git push < remote-name > < branch-a >:< branch-b >

#### git tag
显示所有tag

#### git checkout < tag >
git checkout v0.0.1 ，切换到tag对应的commit

#### git tag -a < tag-name > -m "Some Message"
eg: git tag -a v0.0.3 -m "version 0.0.3"，添加一个新tag

#### git push --tags
同步tags

### Level 6

#### git rebase does 3 things
1）暂存并移除分叉点后的所有commit；2）添加目标branch（默认为origin的对应branch）的所有commit；3）再添加刚才暂存的所有commit

#### git rebase master
master是目标branch；1）移除当前分支commit；2）添加master的新的commit；3）添加刚才移除的commit

#### git rebase --continue
解决冲突后执行。

#### git rebase --skip
跳过这次patch。

#### git rebase --abort
取消当次rebase。

### Level 7

#### git config --global color.ui true
开启色彩。

#### git log --pretty=oneline
一行显示。

#### git log --pretty=format:""
自定义格式。

#### git log --oneline -p
详细地显示增删情况。

#### git log --oneline --stat
显示增删的统计。

#### git log --oneline --graph
图像化地显示commit关系。

#### 时间范围
* git log --until=1.minute.ago
* git log --since=1.day.ago
* git log --since=1.month.ago --until=2.weeks.ago
* git log --since=2012-03-25

#### git diff
* git diff HEAD^
* git diff master develop 查看两个分支的不同

#### git blame
查看文件的每一行是谁来编辑。
* git blame index.html --date short

#### .gitignore

#### git rm file-name
untracked的同时删除该文件

#### git rm --cached file-name
不再track该文件

#### git config --list
查看config

#### alias
`git config --global alias.mylog "log --pretty=format:'%h %s [%an]' --graph"