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
```