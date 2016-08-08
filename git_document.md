![git][git_logo]
# git使用手册
#### 此文中多处链接为[维基百科][wiki]，需要翻墙查看。
---
## 版本控制软件——为什么要使用git
自从高级语言[*Fortran*][fortran]被广泛使用，人类所开发的软件规模爆炸式地增长起来。随之而来的还有大型程序开发与维护中的许多严重问题，这些问题可能导致软件产品的寿命缩短，甚至夭折。这就是所谓的[软件危机][软件危机]。人类在应对软件维基的过程中逐渐总结出一套方法，形成了[软件工程][软件工程]这一学科。其中，一个非常重要的方法就是要对程序进行严格的[版本控制][版本控制]。

版本控制软件就是为了对软件进行版本控制而开发的工具软件。目前常用的版本控制软件有[协作版本系统(CVS)][CVS],[Subversion(SVN)][SVN],[git][git]等。有限元课程之前一直在使用SVN，今年是第一年使用git作为版本管理工具。

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
选择此项意味着可以在Windows的命令行cmd中运行git命令。
![][win_install_6]
Windows中的文本文件格式和Linux/Unix中的文本文件格式[有所区别][win_lin_diff],此选项可以使得git自动进行格式转换。
![][win_install_7]
使用MinTTY的打开Git Bash。这是一个支持多字符集、支持256位色、支持鼠标邮件菜单的强大终端。
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
以下介绍git的常用命令。git的教程资源非常丰富，推荐[廖雪峰的git教程][git_abc]，此教程可完全满足课程需要。感兴趣的同学可以购买相关书籍深入学习。
### git体系简介

[git_abc]: http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/







