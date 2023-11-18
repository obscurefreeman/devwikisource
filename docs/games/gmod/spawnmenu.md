# 添加菜单

## `DMenuBar` （生成菜单上方的菜单条）

下面是我制作的工具箱部分代码的精简版。注意官方维基也有[相关示例](https://wiki.facepunch.com/gmod/DMenuBar)。

`SetIcon`对应的图标请见[官方图标列表](https://wiki.facepunch.com/gmod/Silkicons)。

```lua
hook.Add( "PopulateMenuBar", "oftoolkit", function( menubar )

	local m = menubar:AddOrGetMenu( "晦弗工具箱V2" )	--主菜单
	RunConsoleCommand("r_drawvgui" , 1 )
	m:AddOption("打开晦弗工具箱", function() RunConsoleCommand( "of_menu") end):SetIcon("icon16/wrench_orange.png")
	m:AddCVar( "显示HUD及多余UI", "of_drawhud", "1", "0" ):SetIcon("icon16/attach.png")	   --控制台变量的写法和指令略有不同
	
	m:AddOption( "收拾残局", function() RunConsoleCommand( "of_clean") end ):SetIcon("icon16/cut.png")
	m:AddOption( "重置地图", function() RunConsoleCommand( "of_cleanup") end ):SetIcon("icon16/arrow_refresh.png")
	
	local mdv, mdvOption = m:AddSubMenu( "开发工具" )	   --创建一个二级菜单（开发工具菜单）
	mdvOption:SetIcon( "icon16/monitor.png" )

	mdv:SetDeleteSelf( false )
	mdv:AddOption( "重载模组" , function() RunConsoleCommand( "of_reload") end ):SetIcon( "icon16/arrow_refresh.png" )
	mdv:AddOption( "控制台列出绑键", function() RunConsoleCommand( "key_listboundkeys" )  end ):SetIcon( "icon16/application_xp_terminal.png" )
	mdv:AddCVar( "使用多核渲染", "Gmod_mcore_test", "1", "0" )

	m:AddSpacer()
	m:AddOption( "加血", function() RunConsoleCommand( "of_hpp") end ):SetIcon( "icon16/pill.png" )
	m:AddOption( "自杀", function() RunConsoleCommand( "kill") end ):SetIcon( "icon16/rosette.png" )

end)
```

## `DesktopWindows`（C键菜单）

```lua
list.Set("DesktopWindows", "oftoolmenuc", {
    title = "晦涩弗里曼的工具箱",
    icon = "oftoollogo/oftoollogo.png",	   --图标的路径
    init = function(icon, window)
        RunConsoleCommand( "of_menu")	   --点击后触发的指令
        
    end
})
```

## `PopulateToolMenu`（工具菜单）

下面的这个例子是我的工具箱在生成菜单的的设置面板，这个菜单是可以迁移的，当`of_populatetoolmenu`的值存在且不为0时，这个菜单会被迁移到新的，有自定义图标的工具栏中！

```lua
local function of_populatetoolmenu( pnl )

	pnl:ControlHelp( "工具箱设置" )
	pnl:CheckBox( "将这些菜单迁移到单独的选项卡" , "of_populatetoolmenu" )
    pnl:Help("重启或重载游戏生效。")
    
end

hook.Add( "PopulateToolMenu", "OFMenus", function( )
    if ( GetConVarNumber( "of_populatetoolmenu" ) == nil or GetConVarNumber( "of_populatetoolmenu" ) == 0 ) then
	    spawnmenu.AddToolMenuOption( "Options" , "Obscurefreeman's mod" , "of_populatetoolmenu" , " Main Settings " , "" , "" , of_populatetoolmenu )
    else
        hook.Add("AddToolMenuTabs", "addofpopulatetoolmenu", addofpopulatetoolmenu)
        addofpopulatetoolmenu()
        spawnmenu.AddToolMenuOption( "OFmod" , "Tools" , "of_populatetoolmenu" , " Main Settings " , "" , "" , of_populatetoolmenu )
    end
end )

function addofpopulatetoolmenu()
	return spawnmenu.AddToolTab("OFmod", "OFmod", "gui/silkicons/oftoollogo")
end
```

## 工具菜单里可以添加哪些元素？

[VGUI元素列表](https://wiki.facepunch.com/gmod/VGUI_Element_List){ .md-button }	[搜索VGUI元素](https://heyter.github.io/js-famfamfam-search/){ .md-button .md-button--primary }