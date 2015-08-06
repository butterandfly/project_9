# Git Real 2

## Level 1

### git rebase -i HEAD~3
重新提交最近3个commit。可以通过修改命令文本，可以：
* 改变commit顺序
* 改变commit的message，`reword`
* 将一次commit分成多个，`edit`
* 将多次commit合并成一个，`squash`


## Level 2

### stash
* `git stash`，相当于`git stash save`， 快速保存修改
* `git stash apply`，相当于`git stash apply stash@{0}`，快速恢复最上面的stash项
* `git stash list`，显示所有stash项
* `git stash drop`，相当于`git stash drop stash@{0}`，删除最上的stash项
* `git stash pop`，相当于`git stash apply; git stash drop`

### `git stash apply`时的conflict
若你在修改了一个已经stash的文件，`stash apply`时可能会遇到conflict。通常情况下，你可以这样：

```
git reset --hard HEAD
git stash apply
```

上述情况中若使用pop，对应的stash项不会自动drop掉，你需要手动的drop。

### 某些修改可以commit，某些修改想stash的情况
`git stash save --keep-index`，使stash的时候忽略当前的staging area。

### stash时同时保存untracked的文件
`git stash save --include-untracked`

### `git stash show`可以显示该stash项的相关细节
`git stash show --patch`

### `git stash save "Some Msg"`对stash项添加名字

### `git stash branch <branch-name> <stash-name>`
用当前stash内容新建分支，同时删除该stash。

### `git stash clear`
删除所有stash项。

## Level 3

### 改写history的why和why not

#### Why:

* 侵权问题
* 修改二进制文件
* 隐藏还不能公开的内容

#### Why Not: **

* 所有人都需要更新你的改写
* 没必要

### 改写history前注意备份，因为这可能会丢失内容

### `git filter-branch --tree-filter <command>`
Git会检查每个commit，执行command，再重新commit。例子：
* `--tree-filter 'rm -f passwords.txt'`，删除passwords.txt
* ` --tree-fileter 'find . -name "*.mp4" -exec rm {} \;'`，删除所有mp4
* ` --all `，所有分支

### `git filter-branch --index-filter <command>`
只对staging area其作用。所以command应该是staging中的操作。

### `git filter-branch -f --prune-empty -- -all`
`--prune-empty`会删除没有任何修改的commit。

### 改写history通常包含：
* 从头改动某个文件，或是单纯地在staging中改动，这就需要上面的`--tree-filter`和`--index-filter`
* 改动commit的message，如删去“改动后没有任何修改的commit”，这就需要`--prune-empty`

## Level 4

### `git config --global core.autocrlf input`（mac）
commit时将所有CR/LF（windows）转成LF。

### `git config --global core.autocrlf true`（windows）
LF换成CR/LF（commit时变回LF）。

### 使用.gitattributes

### `git cherry-pick <commit-id>`
合并单个commit（而不是branch）。使用`--edit`修改commit-message。`--no-commit`合并多个commit。`-no-commit`拉取改动并放置在staging area中，但不commit它。`-x`使commit-message更详尽（cherry-pick来之哪里）。`--signoff`对commit签名（添加作者信息）。

## Level 5

### `git submodule add <repo-address>`
添加一个submodule。

### submodule添加一个commit后，父项目中需要重新add和commit来确认改动，因为父项目中需要指明submodule中使用的commit

### `git submodule init`和`git submodule update`
初始化项目中的submodule，然后更新（clone）。

### 项目的更新和submodule的更新需要分开执行
可能你在`git pull`后还需要在`git submodule update`。

### `git submodule update`后submodule的分支会不指向任何一个

### 当在`no branch`做了commit后，checkout时会自动创建一个branch

### submodule修改后的2步
* 在submodule目录中`git push`
* 在项目目录中`git push`

### `git push --recurse-submodules=check`
能在项目push时检查submodule是否已经push。

### `git push --recurse-submodules=on-demand`
自动帮submodules也push。

## Level 6

### `git reflog`
注意它只会保留local的信息。

### `git log --walk-reflogs`
可以在这里找到删除了的commit（或branch）。然后`git branch <branch-name> <commit-id>`来创建回删去了的branch。

## Finish
Further stuff:
* git-scm.com/gitpro
* github help
* git immersion
* git ready
* git cheatsheet
* git flow 和 git-hub flow
