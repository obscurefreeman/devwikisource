---
comments: true
tags:
  - 起源
  - 技术
  - 编程
  - Gmod
---

## 文件结构

这是**本地内容**的基本结构。

```
.
├─ lua/
|   └─ html/
|   |  └─ includes/
|   |     └─ your_local_game.html.lua
|   |     └─ your_multifile_local_game/
|   |        └─ index.html.lua
|   |        └─ script.js.lua
|   |        └─ style.css.lua
|   └─ ofmg_extensions/
|      └─ your_local_games_info.lua
└─ materials/
   └─ entities/
      └─ ofmg_games/
         └─ your_local_game.png
         └─ your_multifile_local_game.png
```

## 处理HTML文件

由于Gmod创意工坊不允许上传`html`文件，我们可以把它伪装成`Lua`文件，并用HTML Loader加载。

- 如果只有一个`html`文件，请把它的后缀改为`.html.lua`放在`lua/html/includes/`文件夹里。

- 如果有多个文件，你可以新建一个文件夹，这里以`your_multifile_local_game`为例，将`html`，`js`，`css`文件全部放进这个文件夹内，然后用`vsc`或记事本（如果你没有`vsc`的话）打开`html`文件，修改`js`和`css`的路径。


### 修改`css`的路径

```html
<link rel="stylesheet" href="your_multifile_local_game/style.css">
```

### 修改`js`的路径

```html
<script src="your_multifile_local_game/script.js"></script>
```

修改完成后，别忘了把`css`文件的后缀改为`.css.lua`，把`js`文件的后缀改为`.js.lua`。

## 填写扩展信息

在`ofmg_extensions`文件夹下创建一个`lua`文件，并尽量用一个独特的名字来命名，以免和别人的扩展冲突。在这个文件里，给`OFMGCustomExtensions`创建一个新的表，并为其命名。同理，给这个表起一个独特的名字。

=== "只有**一个**HTML文件"

    ```lua
    OFMGCustomExtensions["Your Local Game"] = {
        ["Type"] = "Game",--扩展的类型为本地游戏
        ["Info"] = "your_local_game.html",--游戏位置
        ["Image"] = "your_local_game",--图片的名称，请将128*128预览图放在entities/ofmg_games文件夹里
        ["Compatible"] = true,--能否兼容没有安装CEF的Gmod
    }
    ```

=== "含有**多个**HTML文件"    

    ```lua
    OFMGCustomExtensions["Your Multi-file Local Game"] = {
        ["Type"] = "Game",--扩展的类型为本地游戏
        ["Info"] = "your_multifile_local_game/index.html",--游戏位置
        ["Image"] = "your_multifile_local_game",--图片的名称，请将128*128预览图放在entities/ofmg_games文件夹里
        ["Compatible"] = true,--能否兼容没有安装CEF的Gmod
    }
    ```
