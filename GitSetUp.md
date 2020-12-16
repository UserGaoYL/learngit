- [一、安装与设置](#一安装与设置)
    - [1. 前往官网下载安装包](#1-前往官网下载安装包)
    - [2. 按照默认选项安装即可](#2-按照默认选项安装即可)
    - [3. 设置**用户名**和**邮箱**](#3-设置用户名和邮箱)
- [二、创建版本库Repository](#二创建版本库repository)
    - [1. 找一个合适的路径，创建一个空目录](#1-找一个合适的路径创建一个空目录)
    - [2. 通过``git init``命令把创建的目录变成Git可管理的仓库](#2-通过git-init命令把创建的目录变成git可管理的仓库)
    - [3. 把文件添加到版本库](#3-把文件添加到版本库)
- [三、远程仓库](#三远程仓库)
    - [1. 创建SSH Key](#1-创建ssh-key)
    - [2. 设置SSH Key](#2-设置ssh-key)
    - [3. 添加远程仓库](#3-添加远程仓库)


# 一、安装与设置

### 1. 前往[官网下载安装包](https://git-scm.com/downloads, "点击下载")

### 2. 按照默认选项安装即可

### 3. 设置**用户名**和**邮箱**

```
git --global user.name "UserName"           //  UserName 自定义的名字
git --global user.email "email@xxx.com"     //  email 自己的邮箱
```

```
Tips:

git --global 表示这台机器上所有的Git仓库都使用这个配置，当然也可以对某个仓库指定不同的用户和邮箱
```

# 二、创建版本库Repository
### 1. 找一个合适的路径，创建一个空目录
```
mkdir learngit
cd learngit
```

### 2. 通过``git init``命令把创建的目录变成Git可管理的仓库
```
git init
```
这样Git仓库就创建好了，而且是一个空的仓库```empty Git repository```，同时当前目录会多一个``.git``目录，这个目录是用来跟踪版本管理的，千万别修改这里边的文件

### 3. 把文件添加到版本库
   * 编写一个readme.txt，放到第一步创建的目录``learngit``下
   * 用命令``git add readme.txt``告诉Git，把文件添加到仓库（Git暂存区）
   * 用命令``git commit``告诉Git，把暂存区的文件提交到仓库（Git工作区）

   ```
   git commit -m "提交描述"

   Tips:
   -m 后边输入的是本次提交的说明，一定要填写正确的描述，后续方便查看历史记录
   ```


# 三、远程仓库

首先需要有个GitHub账号，如果没有前往[GitHub官网](https://github.com/)注册。
   
本地Git仓库和GitHub仓库之间是通过SSH加密的，所以要设置以下几点：
### 1. 创建SSH Key

在用户主目录下，看看有没有.ssh目录，如果有，再看目录下有没有``id_rsa``和``id_rsa.pub``两个文件，如果有了，直接跳到下一步。

没有的话，打开``Git Bash``创建SSH Key:

```
ssh-keygen -t rsa -C "email.@xxx.com"
```
需要把邮箱地址修改成自己的邮箱，然后一路回车，全部使用默认参数即可，如果一切顺利


可以在用户主目录找到.ssh目录，里边有``id_rsa``和``id_rsa.pub``两个文件，这两个是SSH Key秘钥对，``id_rsa``是私钥，``id_rsa.pub``是公钥

### 2. 设置SSH Key

登录GitHub账号，进入AccountSetting，SSH Keys页面，点击``Add Key``或者``New SSH Key``按钮，

``title``随便输入，Key文本框里粘贴刚刚``id_rsa.pub``里边的内容，然后点击确认即可。

### 3. 添加远程仓库

1. 登录GitHub，点击``Create a new repo``按钮，创建一个新的仓库
