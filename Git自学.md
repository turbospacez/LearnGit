> - [廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)
> - [菜鸟教程Git教程](https://www.runoob.com/git/git-tutorial.html)

# 安装 Git
## Linux
```Linux
git # 查看是否安装git
sudo apt-get install git # Ubuntu/Debian自动安装Git
```

## Windows
- [Git](https://git-scm.com/downloads)
- 右键-Git Bash

```Git
git config --global user.name "NAME"
git config --global user.email "EMAIL@SERVICE.COM"
```
# 创建版本库
> Windows系统, 避免使用中文路径

选择一个文件夹, 右键 Git Bush

**Git本地库初始化**
```Git
git init // 初始化本地库
```

## 编辑工具
- VSC
- VIM
- 不推荐使用记事本(编码问题)

## 添加文件

**将文件添加至仓库**
```Git
git add <file>
```

**将文件提交至仓库**
```Git
git commit -m "<提交说明>" 
```
> 报错：fatal: not a git repository (or any of the parent directories)
> 解决：需要先初始化 git init

**查看工作区当前状态**
```Git
git status
```

**查看文件内容不同**
```Git
git diff <file>
```

**查看文件内容**
```Git
cat <file>
```

## 版本回退
**查看Git日志**
```Git
git log // 完整日志
git log --pretty=oneline // 输出单行日志
git reflog // 记录命令
```
> 回退版本:   git log
> 回新版本:   git reflog

**回退版本**
```Git
git reset --hard HEAD^ // 回退一个版本
git reset --hard commit_id // 返回到指定版本号 可用于回到当前版本
```
> ^代表回退一个版本, ^^表示回退两个版本; HEAD~100回退100个版本

## 工作区和暂存区
**工作区**

电脑中能看见的文件目录, 即当前编辑的版本

**版本库**

工作区的隐藏目录 .git, 作为Git的版本库. 版本库中有：
- 称为stage/index 的 暂存区
- Git 自动创建 master 主分支
- 指向 master 的 HEAD 指针

**Git提交流程**
git add 将文件存入暂存区
git commit 将暂存区内容提交到当前分支的版本库

**Git管理的修改**

如果不将内容 add 缓存库, 就无法 commit 提交代码至版本库

每次git库更改都需要, 先 add 到缓存库, 再 commit 提交代码. 然后 push 到远程库

## 撤销修改
撤销修改内容
```Git
git checkout -- <file>
```
返回最近一次 add 或 commit 提交时的状态

**撤回缓存区代码 已经git add 还没git commit**
```Git
git reset HEAD <file>  // 将缓存区的修改撤销
git checkout -- <file> // 删除工作区的修改记录
```
## 删除文件
```Git
rm <file> // 删除文件命令 或直接文件夹删除
git status // 查看当前文件, 可看删了多少文件
git commit -m "<提交说明>"
```
文件从版本库中删除

**恢复删除文件**
```Git
git checkout -- <file>
```
**如果文件没有被提交至版本库则无法恢复**

且只能恢复最新版本的文件, 会丢失最近一次提交修改的内容

# 远程仓库
1. 创建SSH密钥
      - 用户目录下 .ssh id_rsa.pub 公开密钥
      - 自己创建 SSH Key: ssh-keygen -t rsa -C "email@email.com" 
2. 登录GitHub - Account Setting - SSH Keys - Add SSH Key

GitHub 允许多个 Key, 可以使用不同电脑提交代码

**直接打开ssh文件夹**
```Git
open ~/.ssh
```

## 添加远程库
1. 登录GitHub - Create a new repository - 复制ssh关联地址
2. git remote add origin <关联地址>
3. 本地库内容推送 git push -u origin master
4. 之后推送 git push origin master

> 远程库名字默认 origin


```Git
git remote add origin <关联地址> // Git仓库和远程仓库连接
git push -u origin <分支名> // 第一次推送
git push origin <分支名> // 之后的推送
```

**SSH警告**
第一次链接需要确认是否真的来自GitHub. 需要手动输入 yse

## 删除远程库
```Git
git remote rm <远程库>
```
> 此处删除只是解除本地库和远程库的链接, 如果真的需要删除则需要登录GitHub手动删除

## 远程库克隆
```Git
git clone <关联地址>
```

# 分支管理

## 分支合并
```Git
git branch // 查看分支
git branch <分支名> // 创建分支

git checkout <分支名> // 切换分支
git switch <分支名> // 切换分支

git checkout -b <分支名> // 创建并切换分支
git switch -c <分支名> // 创建并切换分支

git merge <要合并的分支名> // 合并分支

git branch -d <分支名> // 删除分支

git log --graph // 分支合并图
```

> -b 创建并切换

## 解决冲突
1. 自动合并 (无冲突)
2. 手动合并 (手动打开源文件合并)

**手动合并**
```Git
git merge <分支>
```
1. 打开源文件查看冲突内容
2. 手动修改冲突内容
3. 提交

```Git
git add <文件名>
git commit -m "<>"
```
> 此时 commit 不需要输入文件名










