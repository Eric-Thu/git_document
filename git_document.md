![git][git_logo]
# git使用手册
#### 此文中多处链接为[维基百科][wiki]，需要翻墙查看。
---
## 版本控制软件——为什么要使用git
自从高级语言[*Fortran*][fortran]被广泛使用，人类所开发的软件规模爆炸式地增长起来。随之而来的还有大型程序开发与维护中的许多严重问题，这些问题可能导致软件产品的寿命缩短，甚至夭折。这就是所谓的[软件危机][软件危机]。人类在应对软件维基的过程中逐渐总结出一套方法，形成了[软件工程][软件工程]这一学科。其中，一个非常重要的方法就是要对程序进行严格的[版本控制][版本控制]。

版本控制软件就是为了对软件进行版本控制而开发的工具软件。目前常用的版本控制软件有[协作版本系统(CVS)][CVS]，[Subversion(SVN)][SVN]，[git][git]等。有限元课程之前一直在使用SVN，今年是第一年使用git作为版本管理工具。

git相比于SVN具有明显的优势，主要是因为它是一个*分布式*管理系统。这意味着每个开发者的计算机上都有一个完整的仓库，包括完整的源代码以及开发历史。每个开发者需要在自己的仓库内完成自己的工作，形成稳定版本后再上传至远程服务器。这大大减少了开发者之间的冲突，并且对网络的依赖也不如SVN那样严重。

[git_logo]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_logo.jpg
[wiki]: https://zh.wikipedia.org
[fortran]: https://zh.wikipedia.org/wiki/Fortran
[软件危机]: https://zh.wikipedia.org/wiki/%E8%BD%AF%E4%BB%B6%E5%8D%B1%E6%9C%BA
[软件工程]: https://zh.wikipedia.org/wiki/%E8%BD%AF%E4%BB%B6%E5%B7%A5%E7%A8%8B
[版本控制]: https://zh.wikipedia.org/wiki/%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6
[CVS]: https://zh.wikipedia.org/wiki/%E5%8D%94%E4%BD%9C%E7%89%88%E6%9C%AC%E7%B3%BB%E7%B5%B1
[SVN]: https://zh.wikipedia.org/wiki/Subversion
[git]: https://zh.wikipedia.org/wiki/Git
[github]: https://github.com/

## git的安装
推荐使用命令行工具进行git操作，一些git客户端提供简单的GUI，请感兴趣的同学自己查阅资料学习。下面主要介绍不同平台下git命令行工具的安装。
### windows系统
1. 在[此链接][windows_git]下载windows版本的安装程序。
2. 运行安装程序进行安装，相关设置如下图。
![][win_install_3]
这里选择安装git的命令行界面和GUI界面。
![][win_install_5]
选择此项意味着可以在Windows的命令行cmd.exe中运行git命令。
![][win_install_6]
Windows中的文本文件格式和Linux/Unix中的文本文件格式[有所区别][win_lin_diff],此选项可以使得git自动进行格式转换。
![][win_install_7]
使用MinTTY打开Git Bash。这是一个支持多字符集、支持256位色、支持鼠标邮件菜单的强大终端。
3. 安装完成后，在资源管理器中点击鼠标右键，会出现***Git GUI Here***和***Git Bash Here***的选项。
4. 在任意文件夹右键点击***Git Bash Here***选项，在打开的命令行窗口中输入如下命令
```git clone https://github.com/Eric-Song-Love-Coding/git_document.git```
若文件夹中出现`git_document`文件夹，则说明安装成功。你可以在此文件夹中查看此手册的源代码。

### linux系统
1. 打开终端，运行如下命令
```sudo get-apt install git```
即可安装git。
2. 在终端中输入如下命令
```git clone https://github.com/Eric-Song-Love-Coding/git_document.git```
若文件夹中出现```git_document```文件夹，则说明安装成功。你可以在此文件夹中查看此手册的源代码。
[windows_git]: https://git-scm.com/downloads
[win_install_3]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_install_3.png
[win_install_5]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_install_5.png
[win_install_6]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/win_install_6.png
[win_lin_diff]: http://blog.csdn.net/lucky_greenegg/article/details/43232211
[win_install_7]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/win_install_7.png

---

## 简单的Windows cmd命令与linux命令
在使用git时会经常使用Windows cmd和linux中的一些命令，下面介绍一些常用命令。建议在git bash下使用linux命令完成git操作。

###　Windows cmd
在`运行`中输入`cmd.exe`即可打开Windows cmd命令界面。其中输入的均为DOS命令，可以参考[CMD命令速查手册][CMD]。实际使用中常用的所有操作都可以使用鼠标完成。

#### cd命令
显示当前目录名或改变当前目录。

*　`cd`不带参数时，显示当前驱动器和目录。
*　`cd [路径]`可以跳转到制定目录。`..`表示父目录。如`cd c:\learn\git\..\github`。

#### dir命令
显示目录中的文件夹和子目录列表。

---

### Linux
Linux系统有多种发行版，如[Debian][Debian]和[Ubuntu][Ubuntu]。在有GUI的发行版中，需要打开终端才可以输入命令。Linux命令文档可以使用`man`命令查看，也可在[这里][man]，或[这里][man_zh]在线查询。

#### Tab自动补全
Linux终端大多具有自动补全功能。在输入常用命令或参数时，Tab键可以将当前命令或路径自动补全。当有多种补全形式时，还可以自动列出所有可能的方式以供选择。勤用Tab键可以大大提高输入命令的效率和准确率。

#### cd命令
cd命令的功能是切换目录，其参数可以是相对路径或绝对路径。在表示路径时经常要用到以下特殊符号。

* `~`表示主文件夹。`cd ~Eric`表示去到用户Eric的主文件夹，而`cd ~`则表示去到当前用户的主文件夹。同时，`cd`命令也可以直接回到当前用户的主文件夹。
* `..`表示上层目录。如`cd ..`表示回到当前目录的上层目录，`cd /a/b/c/..`表示回到c目录的上层目录，即b目录。
* `-`表示刚才的目录，即上次使用cd命令之前的目录。
* 完整路径/绝对路径。即将路径的全称写出来，以`/`或盘符开头。如`cd /var/spool/mail`或`cd C:\Users\Public`
* 相对路径。直接以目录名开头，指相对于当前路径的路径名。如`cd learn/git/../github`。

####　pwd命令
pwd命令可以显示当前的目录。

####　ls命令
ls可以列出当前目录下所有文件/文件夹的信息。详细参数可以在[此处][ls_man]查看。常用参数说明如下。

* `ls -a`显示所有档案及目录，包括以'.'开头的隐藏文件。
* `ls -l`以长格式显示目录下的内容列表。输出的信息从左到右依次为权限模式、硬连接数、所有者、组、文件大小、文件最后修改时间和文件名。
* `-a`和`-l`等选项可以混用，比如`ls -al`可以显示所有文件的详细信息。

####　mkdir命令
mkdir命令可以在当前目录下新建一个空目录，也可在制定路径下新建空目录。

#### rm命令
rm命令可以删除一个目录中的一个或多个文件夹或目录，也可以将某个目录及其下属的所有文件及子目论均删除掉。使用rm命令删除掉的文件无法恢复，应格外小心。

* `rm -i`删除已有文件或目录之前先询问用户。强烈建议进行删除时加上此选项，系统会要求用户逐一确定是否删除文件。
* `rm -r`递归处理。将指定目录下的所有文件与子目录一并处理。



[Debian]: http://www.debian.org
[Ubuntu]: http://www.ubuntu.org.cn/global
[CMD]: http://www.jb51.net/help/cmd.htm
[man]: http://man.he.net/
[man_zh]: http://man.linuxde.net/
[ls_man]: http://man.he.net/?topic=ls&section=all

---
## git操作
以下介绍git的常用命令。git的教程资源非常丰富，推荐[廖雪峰的git教程][git_abc]，此教程可完全满足课程需要。感兴趣的同学可以购买相关书籍或查阅[官方教程][git_book]深入学习。
### 查看git的帮助文档
git的所有命令都是`git [参数]`的形式，可以使用不带参数的`git`命令就可以列出常用的选项和子命令。
`git help`命令可以得到详细的文档信息，如使用`git help --all`可以获得完整的字命令列表，而通过`git help add`命令可以得到详细的`git add`命令的用法。也可以访问[这个页面][git_doc]来查看在线文档。
### 开始使用git——创建版本库
git的一个重要概念是**版本库（repository）**，版本库只是一个简单的数据库，其中包含所有用来维护与管理项目的修订版本和历史的信息。所有的版本库数据存放在工作目录根目录下一个名为***.git***的隐藏目录中。请注意，*无论何时*都不要删除***.git***目录。
使用git的头一件事就是创建本地版本库。有两种方法可以创建版本库。

* `git init`命令可以将当前目录转化为git版本库，无论文件夹中是否有文件，得到的版本库都是空的版本库，需要将需要的文件添加进去。
* `git clone`命令可以复制（或克隆）一个完整的版本库。此命令会在当前目录下建立一个目录，内含所克隆版本库的副本。git支持一组非常丰富的版本库源，不仅可以通过`git clone git_doc d:\\learn\git_doc`这样的命令克隆本地版本库，还可以支持*ssh*，*http[s]*，*ftp[s]*等协议克隆远程版本库。

建立版本库后，可以使用`git status`命令查看版本库的状态。诸如此时此份文档的版本库状态为下图（此git版本号为2.7.4，运行环境为Ubuntu16.04，可以支持中文）。
![git_status][git_status]
状态信息给出了当前所处的*分支*，与*上游分支*的关系，还说明了当前有未*暂存*的修改，修改还未*提交*。我们将在下文中说明它们的意义。
### 文件的添加与修改
如上文所述，在*/home/eric/learn/test*文件夹下，我们使用`git init`命令简历一个空的版本库。若我们向文件夹中加入*test.txt*文本文件，版本库的状态如下图所示。
![git_add_1][git_add_1]
为了将新文件加入版本库，我们需要使用`git add test.txt`命令。`git add`的参数格式灵活，比如可以使用`git add .`来将当前文件夹下的所有更改都加入版本库。加入文件后版本库的状态如下图所示。
![git_add_2][git_add_2]
git告诉我们，*text.txt*文件已经由“未跟踪的文件”变成了“要提交的文件”。实际上，`git add`命令只是将版本库的修改信息提交到了缓冲区中，并没有建立新的版本，用`git log`命令查看也可以获知当前尚无任何提交。这种设计使得开发者可以多次使用`git add`命令添加修改，甚至是撤回原先的修改，而无须形成过多的版本号。
我们使用`git commit -m '第一次提交'`命令来进行一次提交。提交后版本库状态如下图。
![git_add_3][git_add_3]
`git commit -m`命令中，`-m`作为选项，意为输入本次提交的说明，后面需要输入一个任意的字符串，最好是简单描述本次提交到底做了什么。如果仅仅使用`git commit`命令，git也会提示用户输入提交说明。
在提交后，git生成了一个新的版本号。可以使用`git log`命令查看提交历史，包含了提交的详细信息以及版本号。
在多人合作开发的过程中，还需要知道每次新的版本是由谁来提交的。我们可以在每次提交的命令行中指定身份，但是更方便的方法是使用`git config`命令在配置文件保存身份信息。使用以下两条命令可以设定用户名字和邮箱。
`git config user.name "Eric"`
`git config user.email "songyan_thu@vip.163.com"`
### 分支
git版本库存储了所有的历史版本和修改的记录，其存储结构可以理解成一个“树”状的图（并不等同于离散数学中的“树“），一个典型的版本结构如下图所示。
![git_branch_1][git_branch_1]
图中每个结点均代表了一个版本号。可以看到，我们初始只有主分支（master）上的第一个版本，然后由此版本引出了branchA分支。自此主分支和branchA分支平行前进，互不干扰。主分支在分出branchA分支后，还可以继续分出branchB分支，只不过branchB分支的开始版本与主分支的第二个版本相同。branchA分支依然可以继续分出branchC分支，这些分支依然是平行前进互不干扰的。分支还可以进行合并，如branchA分支的最后并入了主分支，合成了一个新的版本。在分支合并时，主分支上的版本很可能不再是branchA分支分出时的版本，当前版本很可能与branchA分支的当前版本相冲突，这时就需要开发人员解决冲突，git也为我们提供了相关的工具。分支的合并实际上是在两个分支上都进行了一次提交，使得两个分支上的版本相同，而不一定要消灭掉某个子分支。比如branchB与主分支合并后，branchB并没有被删除，而是继续开发。
回到我们建立的版本库test，我们希望在其中的文本文件*text.txt*中写一首小诗。但是由于鄙人才疏学浅思维枯竭，写诗总是要修修改改。这时我们就应当开辟一个写诗的分支，修修改改都在上面进行，只有当满意了才将正式版的诗合并到主分支上。使用`git branch dev`命令建立dev分支，再直接使用不带参数的`git branch`命令就可以查看目前的分支状况，如下图。
![git_branch_2][git_branch_2]
分支状态显示我们当前拥有主分支和dev分支两个分支，而目前处于主分支上（由`*`表示）。使用`git checkout dev`命令可以切换到当前分支上。在此分上我们可以正常进行修改和提交。现在我开始写诗。写完一段诗之后，直接使用`git add`和`git commit`命令就可以在当前分之上提交。
在提交了三次后，我觉得这诗写得……算那么回事了，可以形成一个正式版给别人看看了，这时我就需要将dev分支的合并到主分支上去。为了执行合并操作，需要先使用`git checkout master`命令移回到主分支上。这时我惊讶地发现，*test.txt*文件中我的诗不见了！实际上，`git checkout`命令相当于**检出**了主分支上的最新版本，而写诗的修改全部发生在dev分支中，在主分支中不可见。现在使用`git merge dev`命令就可以将dev分支合并到主分支。
如上所描述的合并只是最简单的情况，在合并时并没有发生冲突，实质上只发生了一次指针的移动，相当于将主分支和dev分支重合起来。可以使用`git log --graph`命令来生成图形化的分支历史记录，如下图。
![git_branch_3][git_branch_3]
可见本次合并后，并没有出现分叉的分支。这是由于合并过程中，git没有检测到冲突，就自动采用了快速合并的方式进行。
现在，我接着在dev分支中进行创作，写了一小段以后我忽然想起来诗竟然没写题目就发布在了主分支中！我只能回到主分支给诗加上题目并提交，然后再回到dev分支中继续创作。当我感觉写得不错，准备向主分支提交时，出现了问题，如下图。
![git_branch_4][git_branch_4]
主分支和dev分支出现了冲突，需要我们手动去处理。打开test.txt文件如下图。
![git_branch_5][git_branch_5]
我们发现发生冲突的地方已经被git使用`<<<<<<<<`、`====`、`>>>>>>>`等符号标出，我们将其改动为正确版本后再提交，就可以将两个分支合并了。合并后使用`git log　--graph --pretty=online --abbrev-commit`命令就可以得到下图所示的分支图。
![git_branch_6][git_branch_6]
现在，我觉得这首诗已经写好了，不需要再修改了，就可以将dev分支删除。删除分支的命令为`git branch -d dev`。使用`git branch`查看可以确认dev分支已被删除。
### 版本回溯
之前，我们已经用`git log`或`git log --graph`查看过版本库的提交历史，图上每个结点都代表一次提交，对应着一个版本号。我们可以利用此版本号来进行版本回溯与快进。
版本回溯的命令为`git reset`。在git中，使用`HEAD`代表当前版本，而`HEAD^`就代表上一个版本，上上个版本当然就用`HEAD^^`代表。所以，当我想回到上一个版本的时候，只需要使用`git reset HEAD^`命令。也可以使用`git reset HEAD~100`命令表示回到１００个版本以前。
> `git reset`命令主要有三个参数，分别为`--soft`，`--mixed`，`--hard`。它们代表了重置当前版本时对索引和工作目录的内容的三种处理方法，git默认使用`--mixed`参数。这三个参数十分重要，建议通过[这个链接][git_reset]来详细了解。

当然也可以直接跳转到某个版本号去。使用`git log --pretty=oneline`命令可以方便地查看版本号和对应的提交信息，如下图。
![git_reset_1][git_reset_1]
与SVN不同，git的版本号不是1.2.3这样递增的数字，而是使用[SHA1][SHA1]算出的一个非常大的数字，使用十六进制表示。只需要使用`git reset [对应的版本号]`就可以跳跃到指定的版本去了。由于散列的离散特性，一般只需要版本号的前几位就可以了。
在版本见跳跃的另一个技巧是，使用`git reflog`命令可以查看git操作历史，包括每条命令是在哪个版本上发出的。这就可以避免错误使用`git reset --hard`命令跳到过去版本回不来了的问题。
![git_reset_2][git_reset_2]
### GitHub和远程仓库
若仅像上文一样在本地管理版本库，相对于SVN等版本控制软件，git并没有显示出多大优势。git的最大优势在于它的分布式特点，而git分布式特征是基于远程仓库来实现的。
远程仓库并不指的是空间上距离足够远（虽然大部分情况确实如此），而是指两个仓库之间通过局域网或者广域网（当然，也可以在同一台计算机中）保持同步的能力。搭建git服务器是容易的，但是对于学生或者个人开发者而言，搭建一个git服务器或许有些小题大做。推荐使用[GitHub][GitHub]来搭建自己的远程版本库，使得自己可以在任意时间任何设备上进行自己的开发。
GitHub是一个**开源**代码库，这意味着任何人都可以在GitHub上注册免费的账号并且托管自己的远程仓库，还可以搜索别人的开源代码来进行学习、使用和开发。GitHub也可以建立私人仓库，但这属于付费功能。
注册GitHub后，就可以在GitHub上创建远程仓库。现在我在我的GitHub中创建poem远程仓库，创建好的界面如下图。
![github_1][github_1]
此界面列出了将远程仓库与本地仓库建立连接的方法，可以看到GitHub支持*https*和*ssh*协议。如果我们想在远程仓库的基础上进行开发，需要将远程仓库克隆到本地；若要将本地仓库推送到远程，则需要在本地仓库手动建立连接。
我们在本地的test仓库中，使用`git remote add origin https://github.com/Eric-Song-Love-Coding/poem.git`命令就可以将本地仓库与远程仓库建立连接。
> git的版本库分为*裸版本库*和*开发版本库*两类。我们之前一直在使用开发版本库，它有工作目录和分支的概念，可以修改和提交。而裸版本库则没有工作目录，它一般作为协作开发的权威焦点。开发人员从裸版本库中进行克隆（clone）、抓取（fetch）和推送（push）更新操作。裸版本库适合作为服务器端的远程仓库。

> 本地仓库与远程仓库的连接是单向的。本地仓库会建立一个连接指回它的父仓库，但是原始版本库并不知道任何克隆版本库。默认情况下，git会将源版本库成为*origin*，其主分支即为*origin/master*。此名称可以更改。

使用不带参数的`git remote`命令可以查看当前连接的所有远程版本库。现在我可以使用`git push -u origin master`命令将当前分支推送到远程库的主分支。如下图所示。
![github_2][github_2]
> 由于我的GitHub并未设置本机的SSH秘钥，所以需要输入账号密码才能够推送。免去这一步骤，可以在GitHub上[进行秘钥设置][SSH_Key]。

`git push`命令有许多选项，这里的`-u`意为将本地主分支和远程版本库主分支绑定在一起，之后只需要`git push origin master`命令即可。注意此命令的格式为`git push [远程版本库名] [本地分支名]`。
当多人合作时，很可能出现这样的情况：在将本地修改推送到远程版本库时，远程版本库已经被他人修改，出现冲突，这时会提示推送失败。所以比较好的习惯就是在每次推送前先使用`git pull`命令抓取远程版本库的最新版本，手动解决冲突后即可推送。

[git_abc]: http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/
[git_book]: https://git-scm.com/book/zh/v2
[git_doc]: https://git-scm.com/docs
[git_status]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_status.png
[git_add_1]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_add_1.png
[git_add_2]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_add-2.png
[git_add_3]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_add_3.png
[git_branch_1]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_branch_1.png
[git_branch_2]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_branch_2.png
[git_branch_3]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_branch_3.png
[bit_branch_4]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_branch_4.png
[git_branch_5]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_branch_5.png
[git_branch_6]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_branch_6.png
[git_reset]: http://www.open-open.com/lib/view/open1397013992747.html
[git_reset_1]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_reset_1.png
[SHA1]: https://zh.wikipedia.org/wiki/SHA家族
[git_reset_2]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/git_reset_2.png
[GitHub]: https://github.com/
[github_1]: https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/github_1.png
[github_2]:　https://raw.githubusercontent.com/Eric-Song-Love-Coding/git_document/master/picture/github_2.png
[SSH_Key]: http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000