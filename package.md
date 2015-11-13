# 软件安装

在 Ubuntu 下，你可以从 `软件源` 安装软件，或是下载 .deb 包进行软件安装。

## apt 的使用方法

### 更新软件包

进行软件包更新前，首先要更新软件源。

    sudo apt-get update

等待软件列表更新完毕后，执行

    sudo apt-get dist-upgrade

进行一键升级。

### 安装软件包

执行以下指令安装 `fpc`

    sudo apt-get install fpc

等待屏幕上显示完软件包信息后输入 Y 即可开始安装。

### 删除软件包

以下指令将会移除 fpc, 然后再移除 fpc 依赖的其他不需要使用的软件包。

    sudo apt-get autoremove fpc

移除软件包时可能会提示 ubuntu-desktop 需要移除。
这时请执行以下指令以免 Ubuntu 桌面环境被删除。

    sudo apt-get remove fpc

由此仅仅删除 fpc

如果不幸移除软件包后发现 Terminal 变小了 (XTerm)，您需要执行以下指令重新安装 Ubuntu 桌面环境。

    sudo apt-get install ubuntu-desktop
