# Git Intro
2020 JI Git Workshop all in one.

[TOC]

## 课前准备

考虑到有些东西没梯子要下到明年，所以提前为大家提供了各种资料：[下载地址]()

有梯子的同学自己去下也可以（相信有梯子同学的水平）。

### 安装Git

#### Windows安装

找到适合自己系统的版本(32位或64位)，运行安装程序即可。安装设置一路next下去即可，只要保证环境变量那一页的设置是第二个就行了。

![git-win-setup](/Users/cheneyni/Desktop/git-intro/img/git-win-setup.png)

#### Mac安装

* 先打开你的terminal尝试输入`git --version`并回车，如果能显示出版本号说明git已经安装（某些版本的mac自带了git），就可以跳过这一部分了。
* 在你的terminal运行`xcode-select --install`安装`Xcode Command Line Tools`。这是Apple官方的一整套开发工具（还包含了gcc，g++）等工具，**推荐使用该方法下载**。下载时间可能较长，建议睡前插着电源让它下载。
* 找到资料包里mac版本的git安装程序，并运行即可。（如果跳出该软件不安全，请前往`设置->安全性与隐私->通用`允许安装包运行。

#### linux安装

参考https://www.git-scm.com/download/linux

会用linux的同学相信你们的水平。

#### 验证安装

安装完成后，打开你的命令行（windows是cmd或者powershell，mac和linux叫terminal），输入`git --version`并回车，如果能看到一行git的版本号说明安装成功。

### 注册一个Github账号

由于其他网站Orgnization人数受限，为了演示和实践方便还是请大家注册一个Github账号。

前往[Github](https://github.com)创建一个账号(Sign Up)

#### 