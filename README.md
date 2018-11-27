# git/repo环境配置

[TOC]

## 安装git

已知ubuntu14.04使用的git（版本1.9）版本过低，配合gerrit（版本2.12）使用有bug，请安装最新的git，命令如下：

```
$ sudo add-apt-repository ppa:git-core/ppa
$ sudo apt-get update
$ sudo apt-get install git
$ git version
git version 2.11.0
```

PS. ubuntu 16.04官方源中的git无此问题，可直接使用`sudo apt-get install git`安装即可。

### 配置Git

请把下面的`yourname`替换为自己的名字和邮箱。

```
$ git config --global user.email "yourname@email.com"
$ git config --global user.name "yourname"
$ git config --global core.editor vim
```

参考：[更多配置](https://git-scm.com/book/zh/v2/%E8%87%AA%E5%AE%9A%E4%B9%89-Git-%E9%85%8D%E7%BD%AE-Git)

### 生成ssh-key

请把下面的`yourname`替换为自己的名字。

```
$ ssh-keygen -t rsa -b 4096 -C "yourname@email.com"
```

之后一直回车即可。执行完毕后生成`~/.ssh`目录，其中保存了一对秘钥（id_rsa.pub为公钥，id_rsa为私钥）

请把生成后的id_rsa.pub发给我们。

## 下载安装repo命令
参考：[Google 官方Repo](https://source.android.com/source/downloading)

如果官网下载不成功，请直接使用我们上传的这个：

```bash
$ mkdir ~/bin
$ PATH=~/bin:$PATH
$ curl https://raw.githubusercontent.com/fukehan/readme/master/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
```

如果贵司没有自己的git-repo，请在~/.bashrc 增加如下：

```
$ export REPO_URL="https://gerrit-googlesource.proxy.ustclug.org/git-repo"
```

这是一个repo url 代理。



## 拉取源码

```
$ repo init --no-repo-verify -u git@github.com:fukehan/manifest.git -b ALPS-MP-N0.MP12-V1.32_DROI8173_TB_N
$ repo sync
$ repo start --all ALPS-MP-N0.MP12-V1.32_DROI8173_TB_N
```

## 重要事项

github 有三个目录没有上传，请完整拉完源码后，手动从其他类似工程拷贝过来，如果没有请联系我用网盘或其他方式共享

1. /prebuilts 整个目录
2. /tools 整个目录
3. /external/eclipse-basebuilder/src/eclipse-sourceBuild-srcIncluded-3.6.2.zip


## 编译项目

```
$ ./mk -d -f pn17662_gb_kttx n
```


