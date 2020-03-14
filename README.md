# Git Intro
2020 JI Git Workshop all in one.

## 课前准备

考虑到有些东西没梯子要下到明年，所以提前为大家提供了各种资料：[下载地址](https://jbox.sjtu.edu.cn/l/SHwJC3)

有梯子的同学自己去下也可以（相信有梯子同学的水平）。

建议你对命令行的基本使用提前有一定的理解，虽然这个workshop不会过多的使用命令行，不看的话问题也不大。这里提供简短的教程：

* [MIT某门课程](https://missing.csail.mit.edu/2020/course-shell/)

* 自行百度（cmd和其他shell会有细微差别，我也没办法给出教程）
* 在这个项目的根目录你还会发现一个叫`python.pdf`的文档，这是我很久以前写的一个python入门教程，里面有一点关于命令行的介绍（有兴趣可以看看

Git教程推荐：

* [非官方教程](https://www.liaoxuefeng.com/wiki/896043488029600)(推荐)
* [菜鸟学堂](https://www.runoob.com/w3cnote/git-five-minutes-tutorial.html)
* [官方教程](https://git-scm.com/book/zh/v2)

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

前往[Github](https://github.com)创建一个账号(Sign Up): 

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/github-sign.png" width="50%" height="50%"/>



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

然后，登陆到Github，去右上角找到你的账号settings里的SSH and GPG keys，选择增加一个新的ssh-key，title可以随便输入你喜欢的名字，底下的打输入框中，复制你刚刚在命令行中打印出来的公钥内容(从"ssh-rsa"开始一直到你的邮箱结束)。然后点击底部按钮即可添加完成。

> Note: 不要复制成你的私钥`id_rsa`。私钥比公钥要长的多。

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-3.png" width="30%" height="30%"/>

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-4.png" width="60%" height="60%"/>

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/ssh-5.png" width="60%" height="60%"/>

#### 验证一下

然后我们简单的验证一下。还是在页面右上角，点击那个加号，选择New Repository，新建一个代码仓库。

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/confirm-1.png" width="30%" height="30%"/>

`Repository name`是你的项目名字，不可以有空格。`Description`是你的项目描述。`Public`代表任何人都能看到这个项目，`Private`代表只有你自己能看到这个项目。最后，建议选择“Initialize this repository with a README”，这样项目创建的时候会自己带一个Readme文件。

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/confirm-2.png" width="80%" height="80%"/>

然后会跳转到新项目的主页，找到页面上唯一一个绿色按钮，点下去，然后再点图中的按钮，将你的项目地址复制到剪贴板。

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/confirm-3.png" width="40%" height="40%"/>

最后，回到你的命令行，依次运行以下命令（#号后面的不用复制）：

```bash
cd ~/Desktop                      # 进入桌面
git clone <your_repo_address>     # clone你刚刚创建的项目
```

注意`<your_repo_address>`要替换成你刚刚复制的项目地址，不要有尖括号或者双引号。

可能会跳出来一个问你是否继续连接的提示，输入`yes`并回车就好了。

然后过了一会，等它运行完成，你就会在桌面上看到一个以你项目为名字的文件夹，内容就是你刚刚创建的项目。至此，说明你安装并配置Git成功了。

现在，**你已经可以使用命令行来操作git并完成所有的版本控制的功能了**。

### 安装一个你喜欢的Git GUI

Git GUI简单来说就是**一类**可以免去你敲命令行的痛苦的桌面软件。它与Git的关系仅仅是锦上添花，没有GUI软件你照样可以用命令行里的Git完成所有操作。当然GUI软件会增加一些实用的工具。

>  GUI软件仅仅是一层壳，它所进行的所有操作仍然是在背后默默的调用命令行里的`git`命令。

这里推荐的GUI有两个：

* Sourcetree (Windows, Mac)
* GitKraken (Windows, Mac, Linux)

这两个总体的界面比较好看，而且易于操作，较为稳定，而且都是免费的。（当然会有付费功能但是不大用得到）

到上面的资料包里面找到对应的版本，然后一步步安装就好了。（还是推荐sourcetree，演示会用，但是GitKraken操作其实是一样的）

* Sourcetree界面：

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/sourcetree.png" width="60%" height="60%"/>

* GitKraken界面:

<img src="https://github.com/JI-git-workshop/git-intro/blob/master/img/kraken.png" width="60%" height="60%"/>

P.S：其实GitKraken的功能强大一点，但是之前它突然开始恰饭了，我就弃用了，改用Sourcetree。但是现在GitKraken好像又不恰饭了💩，所以还是推荐给大家。

### 加入Organization

我创建了一个用来教学和用于Practice的Github组织，你也可以自己创建。

Organization地址：[点这](https://github.com/JI-git-workshop)

完成了上面的课前准备后，请加入这个组织。请将你**注册Github的邮箱地址**发送至我的邮箱: nichujie@sjtu.edu.cn，邮件标题以`[git]`开头。记得查看邮箱，会有邮件让你确认加入组织。

### 扩展练习

待你加入了这个组织后，尝试使用上面的命令（或者GUI）将本项目clone到你的本地（电脑）。