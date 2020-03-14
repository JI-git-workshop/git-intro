# Git Intro
2020 JI Git Workshop all in one.

[TOC]

## 课前准备

考虑到有些东西没梯子要下到明年，所以提前为大家提供了各种资料：[下载地址]()

有梯子的同学自己去下也可以（相信有梯子同学的水平）。

### 安装Git

#### Windows安装

找到适合自己系统的版本(32位或64位)，运行安装程序即可。安装设置一路next下去即可，只要保证环境变量那一页的设置是第二个就行了。

![git-win-setup](https://github.com/JI-git-workshop/git-intro/blob/master/img/git-win-setup.png)

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

由于其他网站Orgnization人数受限，为了演示和实践方便还是请大家注册一个Github账号。(国内上这个网站比较慢，但是等一会还是能出来的，推荐chrome或者firefox浏览器，别用IE就行。有梯子的同学可以开起来了)

前往[Github](https://github.com)创建一个账号(Sign Up): ![github-sign](https://github.com/JI-git-workshop/git-intro/blob/master/img/github-sign.png)



### 简单配置Git

> Note: 从这一步开始，windows用户建议在桌面右键，然后在菜单里面选择**Git Bash Here**。这是一个刚刚下载下来的git自带的命令行。linux和mac还是使用系统自带的terminal。

#### 配置用户名和密码

打开命令行，输入以下两条命令（输一条敲一次回车）:

```bash
git config --global user.name "your_username"
git config --global user.email "your@email.com"
```

注意，`your_username`替换为你刚刚Github账号的用户名，`your@email.com`替换为你注册用的邮箱。（外面的双引号还是要的）

### 配置ssh-key并关联Github

#### 生成ssh-key

简单来说，这一步是为了能让Github验证你的身份，让你能顺利的下载和上传代码。ssh-key是一种密码，通常保存在两个文件中，分别是私钥和公钥。公钥分享给他人，用于验证你的身份；私钥需要自己妥善保存，不可分享给他人。

同样还是在命令行里，运行：

```bash
ssh-keygen -t rsa -C "your@email.com"
```

同样的这里要替换成你刚刚注册用的邮箱。然后会要你依次输入一些信息，如果你不想管，可以一路enter下去。这些依次输入参数的具体含义如下：

* 保存ssh-key文件的路径：默认在~/.ssh下，如果你记不住就不要改。
* Passphrase：密码，一般没什么用，只有在某些需要用到你的key的时候需要输入。一般留空即可。
* 确认Passphrase：如果上一步设置了密码，就再打一遍确认。

![ssh-1](https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-1.png)

当你看到一串奇怪的字符画出现的时候，说明你创建成功了。

#### 上传ssh-key

首先，你需要找到你刚刚创建的key。依次运行以下两条命令：

```bash
cd ~/.ssh
cat id_rsa.pub
```

意义分别是：

* `cd ~/.ssh`: 进入一个叫`.ssh`的文件夹，前面的`~`代表你的用户目录。（如果你是windows且使用了cmd，打开一个新的cmd并且`cd .ssh`即可）
* `cat id_rsa.pub`: 显示文件`id_rsa.pub`的内容，也就是你的公钥。（如果使用了cmd，请将cat换成type)

![ssh-2](https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-2.png)

然后，登陆到Github，找到你的账号settings里的SSH and GPG keys，选择增加一个新的ssh-key，title可以随便输入你喜欢的名字，底下的打输入框中，复制你刚刚在命令行中打印出来的公钥内容(从"ssh-rsa"开始一直到你的邮箱结束)。然后点击底部按钮即可添加完成。

> Note: 不要复制成你的私钥`id_rsa`。私钥比公钥要长的多。

![ssh-3](https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-3.png =300x400)

![ssh-4](https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-4.png)

![ssh-5](https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-5.png)

#### 验证一下

然后我们简单的验证一下

