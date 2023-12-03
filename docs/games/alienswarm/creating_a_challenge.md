---
comments: true
tags:
  - 起源
  - 技术
  - 反应下降
---

# 制作挑战

制作挑战似乎是最简单的部分了。

“挑战”位于`resource/challenges`，在激活时会更改控制台变量 （convar）

## 你可能要用到的变量

* `asw_god` - 值为1时玩家全体无敌

* `asw_controls` - 值为0时是第一人称，1是上帝视角，2是第三人称

* `rd_frags_limit` - 死亡竞赛至少杀死多少人才会赢（这玩意我试了很久，作者似乎套用了一个搜集碎片的变量）

* `rd_deathmatch_loadout_allowed` - 死亡竞赛允许玩家自己选武器而不是必须从地上拣，但改变武器配置会导致战役模式中角色的武器配置改变。这个指令主要是给BOT用的，因为BOT从来不会捡地上的武器，只会一直拿默认枪突突很无聊。

  **此外，死亡竞赛的挑战必须进入游戏后在Tab键菜单激活，否则会不生效（这是个Bug）。**

## 示例

这是官方给出的示例`resource/challenges/cookie9_slippery.txt`，我将注释汉化了一下。

```vdf
"CHALLENGE" {
	"name" "Cookie9's Slippery Floor Challenge"
	"description" "Oh no! The space janitor just washed the floors! They're all slippery!"
	"author" "Cookie9"
	"icon" "swarm/challenges/cookie9_slippery"

	// 如果没有“allowed_mode”，则默认为合作模式挑战。
	"allowed_mode" "coop"
	"allowed_mode" "deathmatch"

	// 添加这一行会使客户端得以下载你的插件，允许你打包模型/纹理/声音/粒子。 
	"required_on_client" "1"

	// 任何控制台变量都可以通过挑战来改变，包括涉及作弊的变量。
	"convars" {
		"asw_marine_friction" "0.2"
	}
}
```

这是我写的一个无友伤+全体无敌的挑战。

```vdf
"CHALLENGE" {
	"name"	"【OF】No friendly fire + God mode|无友伤+全体无敌"
	"description"	"没有友伤+全体无敌"

	"convars" {
		
		"asw_marine_ff_dmg_base" 	"0"
		"asw_marine_ff_dmg_step" 	"0"
		"asw_god" 	"1"	
	}
}
```

我写的无尽死亡竞赛挑战。加上`"allowed_mode" "deathmatch"`可以让你的挑战用于死亡竞赛模式

```vdf
"CHALLENGE" {
	"name"	"【OF】Infinite deathmatch|无尽死亡竞赛"
	"description"	"死亡竞赛时长无限，尽情享受吧！此挑战需要进入游戏后在Tab键菜单激活，否则会不生效！If these challenges are not effective , activate them in the Tab menu after entering the game."
	
	"allowed_mode" "deathmatch"

	"convars" {
	
		"rd_frags_limit" 	"-1"
		
	}
}
```
