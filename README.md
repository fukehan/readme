# repo环境配置

### 生成ssh-key

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


