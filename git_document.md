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

![][win_install_1]
![][win_install_2]
![]


[windows_git]: https://git-scm.com/downloads







