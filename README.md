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
