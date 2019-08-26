# geektime-git

[Git 官方文档](https://git-scm.com/book/zh/v2)

## git 配置

关键词释义：

local 为本仓库；global 当前用户的所有仓库；system 本系统的所有仓库。

优先级：

local > global > system

### 添加配置

```
git config [--global | --local | --system] user.name 'your_name'
git config [--global | --local | --system] user.email 'your_email_address'

# 默认为 local
```

### 查看配置

```
git config --list [--global | --local | --system]
```
### 删除配置

```
git config --unset [--global | --local | --system] user.name
```

## 基本命令

### 创建仓库

```
# 初始化当前文件夹为 git 仓库
git init 

# 创建并初始化该文件夹
git init xxx
```

### 添加暂存区

```
# 添加多个文件
git add xxx xxx xxx

# 将当前目录下的所有变更添加到暂存区
git add .

# 将工作区中已经被 git 管理追踪过的文件变更添加到暂存区
git add -u

# 删除暂存区文件
git rm xxx
```

### 文件重命名

```
# 把 xxx 重命名为 yyy
git mv xxx yyy
```

### 查看历史

```
# 查看简洁的历史（每条历史记录以一行展示）
git log --oneline

# 查看最近 3 次的历史
git log -n3

# 查看所有分支的历史
git log --all

# 展示所有历史添加图形化信息
git log --graph

# 注意：以上命令可以混合使用
```

### 查看帮助

我想一般没人会去看这个……

```
# 跳转到git log 的帮助文档网页
git help --web log
```

## .git 目录

HEAD 文件

config 文件

objects 文件夹

```
# 显示版本库对象的类型（可能是 blob/tree/commit/tag）
git cat-file -t 某个版本的哈希值

# 显示版本库对象的内容
git cat-file -p 某个版本的哈希值

# 显示版本库对象的大小
git cat-file -s 某个版本的哈希值
```

## 分离头指针

```
# commitID 指 commit 的哈希值
git checkout commitID
```

运行上述命令会进入「分离头指针」的状态，在这种情况下修改和提交代码并不会和分支对应起来，当修改和提交代码后如果切换分支，容易丢失刚刚修改和提交的代码。

那「分离头指针」的应用场景是什么？

如果你想基于某个 commit 做变更，尝试一下新方案是否可行，就可以采用「分离头指针」的方式。测试后发现方案不好，可以直接 reset 回其他分支，省却了建/删分支的麻烦。如果觉得新方案有用，那么可以通过用刚提交过的 commitID 新建一个分支出来： `git branch 新分支名称 commitID`，这样即便你切换到其他分支代码也会保留到新建的分支上。

## HEAD 和 branch

HEAD 可以和分支挂钩也可以不挂钩，挂钩时 HEAD 指向该分支的最新 commit ，不挂钩时单独指向某个 commit 就是「分离头指针」的状态。

```
# 比较两个 commit 之间的差异
git diff commitID commitID

# 比较当前指针对应的 commit 与其父亲之间的差异
git commit HEAD HEAD^
git commit HEAD HEAD~1

git commit HEAD HEAD^^
git commit HEAD HEAD~2
```

思考：
> 1 一个节点，可以包含多个子节点（checkout 出多个分支）
>
> 2 一个节点可以有多个父节点（多个分支合并）
>
> 3 ^是~都是父节点，区别是跟随数字时候，^2 是第二个父节点，而~2是父节点的父节点
>
> 4 ^和~可以组合使用,例如 HEAD~2^2

## 删除分支

```
git branch -d 分支名
```
在删除前 Git 会判断该分支上的功能是否被 merge 过，如果报错如下：
```
error：The branch is not fully merged
```

是指这个分支不曾合并到其他任何分支。

在日常开发中，我们通常赋予有意义的分支名，Git判断本分支没和任何别的分支合并，意味这删除存在风险。它也提供我们 `-D` 的方式，如果确定无风险就用 `-D` 。

将 `-d` 改为 `-D` 可以无视上述警告而强制删除分支。

```
# 强制删除
git branch -D 分支名
```

## 修改 commit message

### 修改最新一次 commit 的 message 
```
git commit --amend
```

### 修改任意的 commit message

```
# parentCommitID 指的是要修改的 commit message 的父级 commitID
git rabase -i parentCommitID
```

使用此命令会进入交互式的 git 环境，注意界面上 git 给出的提示






