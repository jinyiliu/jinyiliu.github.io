---
title: 配置Linux新账户
date: 2020-04-03 16:18:23
toc: true
tags:
    - Linux
---

如果有了一个新的服务器账号，按下面的顺序进行操作。

## <span id='SSH'>SSH</span>

配置 `ssh` 免密登录，在本地配置

{% codeblock lang:bash line_number:false %}
ssh-keygen -t rsa            # 生成本地的密钥和公钥匙
ssh-copy-id foo@xx.xx.xx.xx  # 将本地的公钥拷贝到服务器上
{% endcodeblock %}

<!--more-->

在本地编辑`~/.ssh/config`文件配置服务器的信息

{% codeblock line_number:false %}
Host FOO
HostName xx.xx.xx.xx
User foo
IdentitiesOnly yes
{% endcodeblock %}

在本地测试是否能通过`ssh FOO`免密登录。

## Zsh

使用`cat /etc/shells`查看当前可以使用的shell，如果有`/bin/zsh`的一行，可以直接配置

{% codeblock lang:bash line_number:false %}
chsh -s /bin/zsh
{% endcodeblock %}

如果服务器用了NIS系统，需要用`ypchsh`来更改shell。重新登录会有一个简单的Zsh配置过程。然后我们需要安装[Oh My Zsh](https://ohmyz.sh/)来增强Zsh的功能，这样安装

{% codeblock lang:bash line_number:false %}
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
{% endcodeblock %}

注意，有些Oh My Zsh的主题需要取消`conda`默认的环境才能正确的显示

{% codeblock lang:bash line_number:false %}
conda config --set changeps1 False
{% endcodeblock %}


## Git

配置`git`全局的用户名和邮箱

{% codeblock lang:bash line_number:false %}
git config user.name "Jinyi Liu"
git config user.email "liujy0129@gmail.com"
{% endcodeblock %}

使用[SSH](#SSH)中生成密钥公钥的命令，在服务器上生成密钥和公钥并将公钥拷贝到我的[GitHub](https://github.com/settings/keys)仓库里。

## Anaconda

从[清华镜像](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)下载Anaconda3并安装

{% codeblock lang:bash line_number:false %}
wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.3.1-Linux-x86_64.sh
bash Anaconda3-5.3.1-Linux-x86_64.sh
{% endcodeblock %}

可以将上面的Anaconda3链接换成最新的版本，然后安装一些必需的包

{% codeblock lang:bash line_number:false %}
pip3 install pynvim
conda install numpy matplotlib scipy ipython htop
{% endcodeblock %}

需要将tornado的版本回退（参考 [Jupyter-notebook Issue #4630](https://github.com/jupyter/notebook/issues/4630)）

{% codeblock lang:bash line_number:false %}
conda install tornado==5.1.1
{% endcodeblock %}

如果需要建立一个Jupyter notebook服务器，可以参考[如何访问服务器的Jupyter notebook](https://zhuanlan.zhihu.com/p/69869583)。


## **克隆配置文件**

从我的GitHub主页上克隆config这个仓库，并进行一些安装和替换。

## **依赖安装**

NodeJs是NeoVim的依赖。
