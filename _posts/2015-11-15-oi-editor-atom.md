---
layout: post
title:  "Atom 的安装与使用"
date:   2015-11-15
categories: ubuntu
permalink: oiers/editor/atom/
---

Atom: A hackable text editor for the 21st Century

## 安装

    $ wget -O atom.deb https://atom.io/download/deb
    $ sudo dpkg -i atom.deb
    (Reading database ... 299640 files and directories currently installed.)
    Preparing to unpack deb ...
    Unpacking atom (1.2.0) over (1.1.0) ...
    Setting up atom (1.2.0) ...
    Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
    Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
    Rebuilding /usr/share/applications/bamf-2.index...
    Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
    Processing triggers for mime-support (3.58ubuntu1) ...

您就可以在 Dash 中看到 Atom 了。

## 快速启动

按 `Ctrl + Alt + T` 启动 Terminal。

    cd noip-openjudge-program && atom .

就可以在 `noip-openjudge-program` 目录下打开 atom 并编辑该目录下的程序。
