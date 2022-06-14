# Git的使用

## 版本控制

Git主要是分布式版本控制



![image-20220613171754338](https://s2.loli.net/2022/06/14/o9pYOCq3aW7SDtZ.png)

## 环境变量的安装

搜索官网

```
https://git-scm.com/
```

![image-20220613172056864](https://s2.loli.net/2022/06/14/VQi6eOJWr3snM2Y.png)

点击Download下载

![image-20220613172146166](https://s2.loli.net/2022/06/14/TpNUKLyqSCjn8f1.png)

选择自己的版本进行下载

![image-20220613172753218](https://s2.loli.net/2022/06/14/IYMndhO8UvHmTBP.png)

无脑下一步

![image-20220613172839642](https://s2.loli.net/2022/06/14/drARNlmSJjiws29.png)

安装完发现3个程序

Git Bash：Unix和Linux风格相同，使用最多

Git CMD：Windows风格的命令行

Git GUI：图像界面

## 基本Liuxn的基础命令

1）cd：打开目录

2）cd .. ：回到上一目录

3）mkdir  folder：创建文件夹

4）touch file：创建文件

5）mv file path :移动文件到指定的路径

6）rm file ：删除文件

7）rm -r folber ：删除文件夹

8）ls ：查询目录下的全部文件

9）pwd ：查询当前目录地址path

10）clear ：清除命令行

11）reset ：重新恢复Bash

12）exit  ：退出Bash

## Git 的基础设置

### Git的系统config



```bash
所以的Git的系统config都在一个文件下
\Git\etc\gitconfig
```

![image-20220614104903319](https://s2.loli.net/2022/06/14/do3jyghlKiJS2GE.png)

```
Git的Global config也同在
C:\Users\10062\.gitconfig
```

**如果是刚刚下载好的git是没有这些的，或者是找不到该文件**![image-20220614105531649](https://s2.loli.net/2022/06/14/tAyfIJced9rmwh6.png)

### 查看Git配置

```
Git系统配置（System Config）
git config -l （查看全部配置）
git config --system --list(查看系统配置)
Git全局配置（global Config）
git config --global --list（查看个人配置）
```

1) ![image-20220614110025240](https://s2.loli.net/2022/06/14/YRvuIG89iQHyt1J.png)
2) ![image-20220614110245009](https://s2.loli.net/2022/06/14/o2vsgYNR6zfKSde.png)
3) ![image-20220614110447095](https://s2.loli.net/2022/06/14/dROmF2QCywHTKb6.png)

**主要如果刚刚下载Git是没有用户配置的**

### 设置用户配置(重要)

```
git config --global user.name "LuckyNoCat"
git config --global user.email "6666666@qq.com"
```

## Git的工作原理

### 三个区域
Git本地有三个工作区域：工作目录（Working Directory）、暂存区(Stage/Index)、资源库(Repository或Git Directory)。加上远程的git仓库(Remote Directory)就可以分为四个工作区域。文件在这四个区域之间的转换关系如下：

![image-20220614104621918](https://s2.loli.net/2022/06/14/aRLMJ4QXmvHgtDy.png)

1) Workspace：工作区，就是你平时存放项目代码的地方

2) Index / Stage：暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息

3) Repository：仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本

4) Remote：远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换

   

## Git项目搭建

### 本地项目搭建

1，创建全新的仓库用来管理，需要Git管理的项目在本地的根目录执行

```bash
#初始化项目，在当前目录下创建Git代码库
git init
```

![image-20220614111212570](https://s2.loli.net/2022/06/14/jGt9OJ3WcbeA62Q.png)

### 克隆远程厂库

1，还有一种方法是克隆远程目录，将远程仓库的镜像克隆到本地

```bash
#克隆一个项目的代码信息
git clone （url）
```

## Git的文件操作

### Git的四种状态

- **Untracked**:未被跟踪，该文件在文件夹中，但是并没有添加到Git库中，不受版本控制，通过**git add** 状态变为 **Staged**
- **Unmodify**：文件已经入库，未修改，即版本库中的文件快照内容和文件夹的完全一致，这种类型的文件有两种去出，如果它被修改，变为**modified**L，如果使用 **git rm**移除版本库，则成为**untracked**文件
- **Modified**文件已修改，仅仅是修改，并没有进行其他的操作，这个文件也有两个去向，通过**git add**可以进入暂存**staged**状态，使用**git checkout**这丢弃修改过，返回**unmodify**状态，这个**git checkout**即从库中取出文件，覆盖当前修改
- **Staged**暂存状态，执行**git commit**将修改的同步到库中，这时库中的文件和本地文件又变为一致，文件变为**Unmodify**状态，执行**git reset HEAD filenaem**取消暂存，将文件变为**Modified**

```bash
#查看文件的状态
git status

#添加文件到暂存区
git add . #(添加全部文件)

#提交文件到本地仓库
git commit 文件名 -m "提交代码备注" #（提交暂存区的内容到本地仓库）-m 表示提交信息
```

## Github绑定和使用

### 配置SSH公钥

可以在系统盘的用户目录下找到.ssh文件夹

![image-20220614153731377](https://s2.loli.net/2022/06/14/qlIjz2M4vDipw1d.png)

**新的用户的话会没有创建**

在Bash中创建公钥

```bash
ssh-keygen -t rsa #rsa是加密
```

![image-20220614154118781](https://s2.loli.net/2022/06/14/fu8vWcxDdT32zYM.png)

可以发现有了2个文件后缀是.pub的是公钥没有.pub的就是私钥

### 绑定GitHubSSH

然后将公钥的内容全部复制，打开GitHub

![image-20220614154446688](https://s2.loli.net/2022/06/14/BxthKH8D2bv3qu4.png)

点击设置(settings)

![image-20220614154527879](https://s2.loli.net/2022/06/14/KM5x3TGaR7INPAS.png)

然后点击SSh and GPG keys

![image-20220614154611541](https://s2.loli.net/2022/06/14/dfJUWGN2zlXCxIj.png)

点击New SSH key

![image-20220614154816305](https://s2.loli.net/2022/06/14/gKmrROFun32y4SC.png)

![image-20220614154912593](https://s2.loli.net/2022/06/14/YBkALCaS2WsJnQK.png)

输入密码即可。

### 创建GItHub仓库

![image-20220614155726988](https://s2.loli.net/2022/06/14/AQNnzpmwF7BiRJ9.png)

![image-20220614155947761](C:/Users/10062/AppData/Roaming/Typora/typora-user-images/image-20220614155947761.png)
