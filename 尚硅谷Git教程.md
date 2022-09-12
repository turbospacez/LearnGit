> 尚硅谷Git教程
> 
> BV1vy4y1s7k6

# Git概述
免费 开源

**分布式**版本控制工具 / 集中式版本控制工具

本地库、暂存区域、工作流分支

- [Git](https://git-scm.com)

1. 版本控制
    
    记录文件的内容变化, 便于将来查阅特定版本

    最重要：记录文件修改的历史记录, 查看历史版本, 便于回滚

2. 为什么需要版本控制
    
    从个人开发过渡到团队协作, 便于代码合并

3. 版本控制工具

   - 集中式版本控制工具

        单一的集中管理的服务器, 保存所有文件的修订版本

        每个人可以看到项目的其他人在做什么, 管理员也可以掌控每个开发者的权限

        当中央服务器单点故障时, 就无法协同工作

   - 分布式版本控制工具

        每个电脑本地都可以做版本控制(连不上服务器时, 本地也可以保存历史版本), 完成代码后将代码上传至远程库. 其他人在写代码之前要将代码从远程库的仓库完整镜像到本地, 确保代码版本一致.

        - 服务器断网也可以进行开发
        - 每个客户端保存的都是完整项目(包含历史记录)

> 弹幕：应该是git比SVN多了个本地仓库。SVN中央库损坏，历史版本都会没。git中央库损坏，本地库还有历史版本

4. Git历史

Linux系统版本控制历史
   - 1991年 Linus 手动合并代码
   - 2002年 BitKeeper
   - 2005年 Linux社区破解BitKeeper, 回收免费使用权
   - 2005年 Linux自己用 C语言 开发了一个分布式版本控制系统 Git
   - 2008年 GitHub上线

5. Git 工作机制

远程库(代码推送到远程库)
↑ git push
本地库(提交代码 生成历史版本 代码可以回退)
↑ git commit
暂存区(添加 代码可删除)
↑ git add
工作区(存放代码的位置)

6. Git 和 代码托管中心

基于网络服务的远程代码仓库 

代码托管中心 = 远程库

- 局域网
  - GitLab
- 互联网
  - GitHub
  - Gitee (国内)

# Git 安装
- [Git] (https://git-scm.com)

通常使用Git Bash
字体大小调整 CTRL+鼠标滚轮

# Git 常用命令

## 设置用户签名
```git
git config --global user.name <用户名> // 设置用户签名
git config --global user.email <邮箱>  // 设置用户签名
```

Git不会验证邮箱

**检查Git用户签名设置**

C:\Users\当前使用的用户\.gitconfig

用文本编辑器打开, 当时输入的信息被保存到该文件中, 即用户签名设置成功

**该设置仅为本地库的用户签名**

## git初始化本地库
```git
git init // 初始化本地库
```

```linxu
ll    // 查看本地文件
ll -a // 查看隐藏文件
```

## 查看Git状态
```git
git status

On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```

## 本地文件添加暂存区
文件未添加显示红色
文件添加后显示绿色

```git
git add <文件名> // 添加文件至缓存区
git rm --cached <file> // 将文件从缓存区中删除
```

## 提交本地库
```git
git commit -m "版本日志信息" <文件名>

// 初次提交日志
[master (root-commit) 87a4ec1] firstCommit
 1 file changed, 14 insertions(+)
 create mode 100644 git.txt

// 再次提交日志
nothing to commit, working tree clean
```

```git
git reflog //查看引用日志信息
git log    //查看详细信息日志
```

## 修改文件
```git
cat <文件名> // 查看文件内容

git commit -m "日志" <文件名> // 提交文件

git reflog
cd63aa8 (HEAD -> master) HEAD@{0}: commit: secondCommit
87a4ec1 HEAD@{1}: commit (initial): firstCommit


```

## 历史版本
```git
git reflog // 仅显示文件特征码
git log    // 显示每次版本提交的用户签名 日期


git reset --hard 特征码 // 回退版本
```

> 复制 Ctrl + Ins
> 粘贴 Shift+ Ins
> 选中复制内容 单击鼠标中键 直接粘贴
> 选中复制内容 Shift + Ins 直接粘贴

**检查版本**
1. git reflog
2. 本地文件查看
   1. git文件目录\\.git\head 查看 目前分支
   2. git文件目录\\.git\refs\heads\master

# git分支操作
## 什么是分支
同时推进多个任务, 就可以给每个任务创建的单独分支

## 分支的优势
- 可以同时开发多个功能, 提高开发效率
- 如果其中一个分支开发失败, 不会影响项目中的其他分支

## 分支操作
```git
git branch <分支名>     // 创建分支
git branch -v           // 查看分支
git checkout <分支名>   // 切换分支
git merge <分支名>      // 指定分支合并到当前分支
```

# Git 团队协作机制
```git
git pull  //将代码从远程库拉取至本地库
git push  //推送至远程库
git clone //协作开发的人从远程库克隆代码至本地库
git fork  //将他人远程库代码复制至自己远程库
git pull request // 提交代码至主远程库
```

## 团队内协作 (共用一个远程库)
pull 拉取代码
push 推送代码

clone 将远程库代码克隆至本地库

push 推送本地库代码至远程库

## 跨团队协作 (多个远程库)
fork 复制远程库

pull request 远程库推送至主远程库

merge 主远程库将代码合并

# - [GitHub](https://github.com)
页面右上角 - Create a new repository
https://github.com/turbospacez/LearnGit.git