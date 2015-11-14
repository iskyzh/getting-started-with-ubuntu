# Ubuntu 的软件安装

在 Ubuntu 下，您可以从 `软件源` 安装软件，或是下载 .deb 包进行软件安装。

## apt-get (Advanced Package Tool)

> 高级包装工具（英语：Advanced Packaging Tools，缩写为APT）是 Debian 及其派生发行版的软件包管理器。
> APT 可以自动下载，配置，安装二进制或者源代码格式的软件包，因此简化了 Unix 系统上管理软件的过程。
> APT 最早被设计成 dpkg 的前端，用来处理 deb 格式的软件包。现在经过 APT-RPM 组织修改，
> APT 已经可以安装在支持 RPM 的系统管理 RPM 包。

### 更新软件包

进行软件包更新前，首先要更新软件源。

    $ sudo apt-get update

等待软件列表更新完毕后，执行

    $ sudo apt-get dist-upgrade

进行一键升级。

### 安装软件包

执行以下指令安装 `fpc`

    $ sudo apt-get install fpc

等待屏幕上显示完软件包信息后输入 Y 即可开始安装。

### 删除软件包

以下指令将会移除 fpc, 然后再移除 fpc 依赖的其他不需要使用的软件包。

    $ sudo apt-get autoremove fpc

移除软件包时可能会提示 ubuntu-desktop 需要移除。
这时请执行以下指令以免 Ubuntu 桌面环境被删除。

    $ sudo apt-get remove fpc

由此仅仅删除 fpc

如果不幸移除软件包后发现 Terminal 窗口变小了 (XTerm)，或是看见 apt 正在移除 unity 等包，
您需要执行以下指令重新安装 Ubuntu 桌面环境。

    $ sudo apt-get install ubuntu-desktop

## ppa (Personal Package Archives)

> A Personal Package Archive (PPA) is a special software repository for
> uploading source packages to be built and published as an APT repository by
> Launchpad. While the term is used exclusively within Ubuntu, Launchpad host
> Canonical envisions adoption beyond the Ubuntu community.

添加 ppa 等同于向您的 Ubuntu 中添加一个自定义软件源。这个软件源中的二进制包存放在
[launchpad](https://launchpad.net/ubuntu) 上。

### 添加 ppa 源

    $ sudo add-apt-repository ppa:numix/ppa
    The official PPA for the Numix Project - http://numixproject.org

    The PPA consists of various artwork packages from the Numix Project.
    More info: https://launchpad.net/~numix/+archive/ubuntu/ppa
    Press [ENTER] to continue or ctrl-c to cancel adding it

    gpg: keyring `/tmp/tmpw9wuror8/secring.gpg' created
    gpg: keyring `/tmp/tmpw9wuror8/pubring.gpg' created
    gpg: requesting key 0F164EEB from hkp server keyserver.ubuntu.com
    gpg: /tmp/tmpw9wuror8/trustdb.gpg: trustdb created
    gpg: key 0F164EEB: public key "Launchpad PPA for Numix Maintainers" imported
    gpg: Total number processed: 1
    gpg:               imported: 1  (RSA: 1)
    OK

### 安装 ppa 源中的包

    $ sudo apt-get update
    $ sudo apt-get install numix-gtk-theme
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages will be upgraded:
      numix-gtk-theme
    1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
    Need to get 53.2 kB of archives.
    After this operation, 78.8 kB of additional disk space will be used.
    Get:1 http://ppa.launchpad.net/numix/ppa/ubuntu/ wily/main numix-gtk-theme all 2.3+344~201508102301~ubuntu15.10.1 [53.2 kB]
    Fetched 53.2 kB in 5s (10.2 kB/s)          
    (Reading database ... 299640 files and directories currently installed.)
    Preparing to unpack .../numix-gtk-theme_2.3+344~201508102301~ubuntu15.10.1_all.deb ...
    Unpacking numix-gtk-theme (2.3+344~201508102301~ubuntu15.10.1) over (2.3+344~201508102301~ubuntu15.04.1) ...
    Setting up numix-gtk-theme (2.3+344~201508102301~ubuntu15.10.1) ...

### 卸载 ppa 源中的包

与 apt-get 的使用相同。

## dpkg

> dpkg 是 Debian Package 的简写，由 Debian 发行版开发，用于安装、卸载和供给和 deb
> 软件包相关的信息。

### 使用 dpkg 安装包
