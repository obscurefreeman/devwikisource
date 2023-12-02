---
comments: true
tags:
  - 起源
  - 技术
  - 编程
  - 地图
  - Gmod
---

# 为Garry's Mod制作简单的模组

我的Gmod编程是自学的，因此本页指南只能作为学习笔记参考。如果你有机会详细学习`Lua`，请无视这些较为基础的教程。

## 准备

在开始制作Garry's Mod模组前，你需要在电脑里安装**[gmpublisher](https://github.com/WilliamVenner/gmpublisher)**和**[VSC](https://code.visualstudio.com/download)**。

之前我们用游戏文件夹里的`gmad.exe`程序打包模组，写批处理文件发布模组，这很繁琐。但有了`gmpublisher`之后，我们可以轻松地发布和管理自己的模组，当然，它还有一个重要的功能——下载和解包其他人的模组，看看大佬是怎么做模组的。

至于VSC，我相信你知道它是用来干什么的。别忘了给它安装`Glua`扩展，该扩展可以标注Garry's Mod的语法，对编程很有用。

## 插件文件夹

相信经常装插件的朋友们对插件文件夹一定不陌生，它位于路径`GarrysMod\garrysmod\addons`中，你可以将你的整个插件文件夹直接拖入这个文件夹内，而无需将其打包成`gma`文件

## 客户端和服务器

在[Garry's Mod Wiki](https://wiki.facepunch.com/gmod/)中，很多词条前有蓝色和黄色的色块，这些色块蓝色代表服务器，黄色代表客户端，而在你的模组文件夹的`autorun`文件夹中，`server`文件夹中的代码会在服务器状态下运行，`client`文件夹中的代码会在客户端状态下运行
