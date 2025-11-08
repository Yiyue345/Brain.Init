# Git 安装 & GitHub 基本用法
---
> [!INFO]
> 这篇文章旨在介绍 Git 与 GitHub 的使用，但由于内容与排版较为混乱，将来可能会发生大量更改或完全重写
> 

## 1.进不去 GitHub？

由于某些特殊的原因 ~~（指 GFW）~~ ，我们直接连接 GitHub 大概率是要看运气的。如果需要稳定访问，可以使用 [Steam++](https://steampp.net/) 或其他工具进行加速，亦可前往科协连接科协 WiFi 使用
## 2.注册 GitHub

在学习 git 之前，我们先注册一个 GitHub 账号

##### 1.登陆 GitHub

前往 [GitHub 官网](https://github.com/) ，点击官网右上角的 sign up 进行注册

![image-20250517111736145](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517105937198.png)

##### 2.按照所给格式填写相关信息

之后证明自己是人

![image-20250517111736145](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517111736145.png)

在邮箱中找到验证码

![image-20250517111840296](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517111840296.png)

输入验证码后，你就创建好 GitHub 账号了！请记住你所绑定的邮箱，和设置的密码。

## 3.在 GitHub 中创建仓库

现在你已经有了一个 GitHub 账号了。在正式开始学 git 之前，我们要在 GitHub 先创建一个远程仓库

仓库嘛，顾名思义就是一个存放代码的地方，方便大伙把代码整合到一起

点击 GitHub 网页界面右上角的头像，点击 **Your repositories**（你的仓库）

![image-20250517115948705](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517115948705.png)

目前你还没有任何仓库，让我们来 new 一个，点击绿色按钮 **new** 一个新的库

![image-20250517120047861](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517120047861.png)

**我们进入了一个新的界面！现在我们就要编辑库的基本信息了，让我们一个一个来看看这些都是什么**

![image-20250517120122171](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517120122171.png)

**Repository name**，正如其名，这是你的仓库名，**给你的仓库起一个易识别的名字**

**Description**，可以给你的库做一个简单的**介绍**

**public** （公共的）和 **private** （私有的）是这个库的**访问权限**

##### **add a README file**，README 会显示在库的最下方，**一般是用来介绍这个库是做什么用的**，以及如何使用

**Add .gitignore**  **这个很重要**， .gitignore 可以帮助你把不需要添加到仓库中的文件过滤（如配置文件等），可以节省上传时间，让仓库变的干净等，**这个选项根据这个库的类型进行选择**

**Choose a license** 主要用于指导你在项目中添加一个合适的开源协议，**默认为 None 就好**

以下是一个创建选项的参考 

![image-20250517120610821](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517120610821.png)

**好了！现在我们已经把仓库的基本设置完成了，点击Create repository就可以正式创建一个库了！**

## 4.学习 Git

目前我们已经把 GitHub 端的基本操作完成了，接下来要做的就是正式开始学习 git

关于 git 的基本操作，我会在具体实践的过程中讲解。

##### 安装 Git

https://git-scm.com/downloads
进入网址后，按照电脑的系统进行 git 安装

![image-20250517122124404](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517122124404.png)

​																				![image-20250517122144975](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517122144975.png)

之后就会进行下载，下载完成后打开 .exe 安装包，安装时**全部选择默认选项**即可

![image-20250517122232086](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517122232086.png)

点击 install，等待安装，安装后就完成了

##### 如果你已经有了想上传到 GitHub 的文件，请依照下面的教程进行操作

首先，找到你想要上传到 GitHub 的本地文件目录，点击 **"查看/展示"** ，勾选 **“隐藏的项目"**

![image-20250517121946574](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517121946574.png)

接下来就可以进行 git 仓库的**初始化**了

##### 文件夹初始化

**右键点击空白处**，选择在终端中打开

![image-20250517122701485](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517122701485.png)

如果没找到，**点击显示更多选项**，在里面找到 **“在终端中打开”**
点击后，会有一个控制台窗口，**git 的指令都会在这个窗口中进行**		

![image-20250517122815793](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517122815793.png)

首先，我们对文件夹进行初始化。输入`git init`，并回车


![image-20250517122902570](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517122902570.png)

这时我们返回文件夹，就会看到有一个被隐藏的 .git 文件，因为之前我们已经设置了**显示隐藏文件**，所以我们可以看到这个 .git 文件夹

![image-20250517122940148](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517122940148.png)

这样就算完成了本地仓库的初始化！

接下来我们要做的是**关联远程仓库**，其实就是把本地仓库和远程仓库连接起来。

**输入**`git remote add origin https://github.com/用户名/仓库名.git`

origin 后面的就是你的仓库地址，如下图演示

![image-20250517123440895](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517123440895.png)

把这个地址复制过来，在终端中输入

![image-20250517123706035](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517123706035.png)
如果没有弹出任何报错信息，那就代表成功了！我们再次验证一下：**输入** `git remote -v`

![image-20250517123803933](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517123803933.png)
我们可以看到，目前本地和远程已经成功绑起来了！

下面，我们需要把远程的.gitignore文件拉取到本地。之所以要在提交之前拉去 .gitignore 文件，是为了让我们第一次提交的时候也保持文件的整洁

**接下来的拉取会有两种形式，权衡利弊后选择自己喜欢的一种。**

##### 1.每次都手动拉取 main 分支

**输入**`git pull origin main`
拉取main分支上的所有文件

![image-20250517124231130](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517124231130.png)

##### 2.设置分支跟踪（只需要一次）

**输入**`git branch --set-upstream-to=origin/main main`
这样 main 分支以后默认跟踪远程 origin main 了，**之后用 git pull 就能够自动合并**

![image-20250517124435052](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517124435052.png)

这样我们就成功的把远程的文件拉取到本地了！查看我们的本地文件夹，就发现多了 .gitignore 和 README 文件

![image-20250517124311866](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517124311866.png)

**接下来我们要开始添加文件了**
**输入** `git add .` 
(这里还有一个点，实际上就是 git[空格]add[空格].   add和.之间有一个空格)
`git add .`是将此文件夹中除了 .gitignore 忽略文件以外的所有文件全部添加到暂存区。

（或者你只想添加指定的文件，可以 git add 文件名，如 git add KexieGitTest.doc）

![image-20250517124752096](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517124752096.png)

接下来我们就要把暂存区的文件提交到本地仓库了，我们使用最简洁的提交方式
**输入**`git commit -m "此处为提交描述"`  
（注意，格式为git[空格]commit[空格]-m[空格]"此处为提交描述"）

![image-20250517125021447](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517125021447.png)

成功了！我们把文件上传到本地仓库了！
接下来就是把本地仓库中的文件推送到远程仓库。

如果在之前你已经设置了**分支跟踪**，那么你只需要
**输入** `git push`
反之，则需要输入`git push origin main`，才能成功提交到远程

![image-20250517125644081](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517125644081.png)

好了！这样你就会在 GitHub 中看到你所上传的所有文件了！ 

## 5.团队协作篇之fork & pr

*现在要开始团队协作了吗？*

首先，去到想要参与的 GitHub 仓库页面，点击右上角的 **Fork** 按钮，把该项目的副本复制到自己的仓库

![image-20250517130550810](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517130550810.png)



![image-20250517130559950](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517130559950.png)

完成！现在你就可以返回到你的仓库中，找到你刚刚 Fork 的项目了！！


![image-20250517130652064](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517130652064.png)

![image-20250517130702830](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517130702830.png)

现在，我们要做的是把远程仓库中的所有代码 clone 到本地
首先，创建一个新的文件夹，在文件夹中的空白处点击右键，**“在终端中打开”**

![image-20250517130926088](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517130926088.png)

在终端中，把远程文件 clone 到本地
输入`git clone 文件目录`
如下图举例

![image-20250517131105928](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517131105928.png)

![image-20250517131114239](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517131114239.png)

这样就把远程中的文件 clone 到本地了！我们来看一下

![image-20250517131143030](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517131143030.png)

和远程的文件一模一样！

接下来，我们要配置上游仓库。你 Fork 的项目会随着时间变化，仓库可能会不断更新。为了能同步这些更新，你就需要配置  upstream。

首先，添加原始仓库作为你的 upstream（就是你fork仓库的主人）如下图所示

![image-20250517131950789](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517131950789.png)

**输入** `git remote add upstream 原始仓库地址`


![image-20250517132259072](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517132259072.png)

和之前验证本地绑定一样，输入 `git remote -v`验证是否绑定成功

![image-20250517132333420](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517132333420.png)

我们可以看到已经绑定成功了！

绑定成功后，我们来在本地创建一个分支。

**关于分支，我推荐 main 只同步上游，只保留最稳定的版本，所有的功能开发和 bug 修复都在 feature 分支上完成，完成之后发 pr，合并到主分支**

**输入**`git checkout -b feature/分支名`
（也可以不用前面的feature， feature/分支名只是一种命名规范）
如下图

![image-20250517133649638](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517133649638.png)

我们成功在本地创建了一个新的分支！并且checkout（切换）到了这个分支当中，之后的功能开发都要在分支当中进行

**接下来我们要在 feature 分支上写代码，写完代码后我们进行提交**
**老样子**，`git add .`     `git commit -m "实现内容"`

![image-20250517133857692](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517133857692.png)

我们成功的把文件添加到了本地！
接下来就是要把 feature 分支推送到自己的仓库

**输入**`git push origin feature/分支名`
这样就可以在 GitHub 中看到自己的分支了

![image-20250517134124275](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134124275.png)

我们前往自己的分支看一下


​	![image-20250517134146739](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134146739.png)

一切正常！我们刚写的代码也成功的上传到了分支当中！

**如果你的分支功能已经稳定，想要更新自己仓库中的 main 了，就要在本地切回 main 分支，进行合并**
输入`git checkout main`，切回 main 分支

​					![	](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134336626.png)									
我们成功的切换到了 main 分支上！

接下来要合并 lny 分支和 main 分支

**输入**`git merge featrue/分支名`

如下图所示

![image-20250517134440380](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134440380.png)

我们成功的在本地把 lny 分支的更改合并到了 main 分支！

再把本地的修改推送到远程，**我们利用手动拉取main分支的方法**

**输入**`git push origin main`

​					![image-20250517134558998](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134558998.png)
成功了！让我们检查 GitHub 的 main 分支是否更新

![image-20250517134637859](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134637859.png)

![image-20250517134649235](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134649235.png)

更新成功！现在 git 方面的代码已经基本完善了，接下来就要交 pr 等待库的拥有者同意合并了！

我们回到 GitHub，准备 Pull requests 的工作

回到自己的库中，选中main分支，点击 **Pull requests**

![image-20250517134839415](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134839415.png)

点击**new pull request**


![image-20250517134901795](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517134901795.png)

接下来就可以看到我们的提交信息，以及是否和源库中有冲突。如果开发分支与上游主分支有冲突，我们需要手动去解决冲突，这个我们后面再讲。目前我们的代码没有任何的冲突，就可以去 **Create pull request** 了

![image-20250517135201335](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517135201335.png)

之后来添加描述
![image-20250517135219107](https://raw.githubusercontent.com/Concorde0/image/refs/heads/main/image-20250517135219107.png)

点击 Create pull request，就可以向上游主分支拥有者提交合并请求了！
到这里，你就完成了所有关于团队协作的部分了！

## 6.超级注意事项！！！

#### 	**无论什么时候，在你写代码之前，一定要及时拉取上游主分支的一切改动，同步上游主分支代码到本地，具体操作如下**

##### 1.切换到本地main分支

`git checkout main`

##### 2从上游仓库拉取最新代码

`git fetch upstream`

##### 3把上游的main合并到本地

`git merge upstream/main`

##### 4把更新后的main推送到远程仓库

`git push origin main`

##### 5.切换到工作分支 比如我这里的  feature/lny

`git checkout feature/lny`

##### 6.把从上游仓库的最新代码合并到你的功能分支，更新功能分支代码

`git merge main`

#### 如果新代码和你的功能分支代码有冲突，就要手动编辑解决冲突！！

##### 7.解决冲突后，把更新后的功能分支推送到远程仓库

`git push origin feature/lny`


## 7.关于规范

#### 1.命名规范

不同的语言，不同的项目有着不同的命名规范，比如 C# 中，private 字段前要有下划线 _ 来区分这个字段的访问权限

#### 2.提交和pr规范

##### 提交一般要有清晰的提交信息，采用规范的格式，如下所示

feat: 添加用户登录功能

fix: 修复无法保存设置的 bug

refactor: 重构登录逻辑

docs: 更新文档

**在PR中要描述清楚改动的目的和影响，每个功能都要用pr提交**

#### 3.Issue的使用

可以用 Issue 来记录 bug ，功能需求等