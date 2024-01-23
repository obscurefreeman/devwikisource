---
comments: true
tags:
  - 起源
  - 技术
  - 编程
  - Gmod
---

## 文件结构

=== "这是**在线游戏**的基本结构"

    ```
    .
    ├─ lua/
    |  └─ ofmg_extensions/
    |     └─ your_online_games_info.lua
    └─ materials/
       └─ entities/
          └─ ofmg_games/
             └─ your_online_game1.png
             └─ your_online_game2.png
             └─ your_online_game3.png
    ```

=== "这是**网站**的基本结构"

    ```
    .
    ├─ lua/
    |  └─ ofmg_extensions/
    |     └─ your_websites_info.lua
    └─ materials/
       └─ entities/
          └─ ofmg_websites/
             └─ your_website1.png
             └─ your_website2.png
             └─ your_website3.png
    ```

## 填写扩展信息

在`ofmg_extensions`文件夹下创建一个`lua`文件，并尽量用一个独特的名字来命名，以免和别人的扩展冲突。在这个文件里，给`OFMGCustomExtensions`创建一个新的表，并为其命名。同理，给这个表起一个独特的名字。

=== "这是**在线游戏**的扩展信息示例"

    ```lua
    OFMGCustomExtensions["Your Online Game"] = {
        ["Type"] = "Game online",--扩展的类型为在线游戏
        ["Info"] = "https://online-game/",--玩游戏的网站
        ["Image"] = "your_online_game1",--图片的名称，请将128*128预览图放在entities/ofmg_games文件夹里
        ["Compatible"] = true,--能否兼容没有安装CEF的Gmod
    }
    ```

=== "这是**网站**的扩展信息示例"    

    ```lua
    OFMGCustomExtensions["Your Website"] = {
        ["Type"] = "Website",--扩展的类型为网站
        ["Info"] = "https://your-website/",--网站链接
        ["Image"] = "your_website1",--图片的名称，请将128*128预览图放在entities/ofmg_websites文件夹里
        ["Compatible"] = true,--能否兼容没有安装CEF的Gmod
    }
    ```