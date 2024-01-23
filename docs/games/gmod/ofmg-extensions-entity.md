---
comments: true
tags:
  - 起源
  - 技术
  - 编程
  - Gmod
---

# 制作实体

将你的画面投射到任何模型上。

## 文件结构

这是`实体`的基本结构。

```
.
├─ lua/
|  └─ entities/
|  |  └─ your_entity/
|  |     └─ ...
|  └─ ofmg_extensions/
|     └─ your_entity_info.lua
└─ materials/
   └─ entities/
      └─ your_entity.png
```

## 填写扩展信息

在`ofmg_extensions`文件夹下创建一个`lua`文件，这里我将其命名为`your_entity_info.lua`，不过请记住尽量用一个独特的名字来命名，以免和别人的扩展冲突。

```lua
OFMGCustomExtensions["Your Entity"] = {
    ["Type"] = "Entity",--类型为实体
    ["Info"] = "your_entity",--填写你的实体名称
    ["Compatible"] = true,--能否兼容没有安装CEF的Gmod
}
```

## 撰写实体代码

获取被激活的画面并且判断是在线内容还是本地内容。


```lua
local page = ofmgactivate

if string.sub(page, 1, 4) == "http" or string.sub(page, 1, 6) == "asset:" then
    self.Panel:OpenURL(page)
    --如果是在线内容则打开网页。
elseif string.sub(page, -5) == ".html" then
    self.Panel:OpenFile(page)
    --如果是本地内容则打开文件。
else
    self.Panel:OpenFile("gamescreen.html")
    --如果没有设置则打开默认本地网页。
end
```

将画面投影到屏幕上。

```lua
function ENT:Draw()
	self:DrawModel()

	self.ScreenOrigin = self:LocalToWorld(Vector(6,-28.9, 35.7))
	--屏幕的位置
	cam.Start3D2D(self.ScreenOrigin, self:LocalToWorldAngles(Angle(0,90,90)), 0.0304)
		self.Panel:PaintManual()
    	--绘制面板
	cam.End3D2D()
end
```

