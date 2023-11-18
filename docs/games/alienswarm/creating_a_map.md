# 制作地图

在初次为《反应下降》制作模组时，我雄心勃勃地选择了CSGO地图“湖畔激战”作为移植对象。在一个大家耳熟能详的第一人称游戏地图里用上帝视角打死亡竞赛体验会怎么样呢？

然而，让人难以忍受的是，《反应下降》不支持harmmer++，编辑《反应下降》地图仅能使用官方的SDK工具。在Steam库中搜索Reactive Drop，找到官方SDK，下载后重新打开《反应下降》的游戏文件夹，你能发现`bin`中多了一些开发工具，找到harmmer打开。

![20231118161932.png](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/20231118161932.png)

如图，《反应下降》的info_player_start的模型是一个穿着海军陆战队服装的戈登 · 弗里曼。

![20231118162013.png](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/20231118162013.png)

另一种玩家出身点，是死亡竞赛一种对抗模式的一方的出生点。

![20231118162134.png](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/20231118162134.png)

一种信息节点，开发者建议在死亡竞赛中使用这种节点，防止bot呆在原地不动。

《反应下降》的地图制作和其他起源引擎游戏类似，尽管游戏内大多数地图没有3D天空盒（因为玩家正常游戏时是看不到天空的），你仍然能为地图制作天空盒，并且它们能完美显示。

但当我完成这张地图开始编译时，某些东西开始出错了。

## 这又是怎么回事？

游戏变成了全亮模式，并且一些不该显示的笔刷也显示了。

![20230910152634_1.jpg](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/20230910152634_1.jpg)

经过我三番五次地推断后，我忍不住把整张地图封了起来，然而编译结果仍然没有任何变化，难道不是因为地图泄露？

在和开发者讨论后，我得到了一个完美的答复。

![entity-structure.png](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/entity-structure.png)

## 罪魁祸首浮出水面

由于《反应下降》的vvis具有 `-alldetail` 参数，引擎会把所有固体转化为`func_detail`，因此你需要把套住地图的大盒子转为`func_brush`并命名为`structure_seal`，其余不想被转为`func_detail`的实体也应这么操作且命名必须以`structure_`开头。

## 题外话：小地图

《反应下降》的小地图与《CSS》和《CSGO》的雷达图原理完全相同，如果你想移植只需拷贝图片和偏移量数据！

在下面的几张图片中，从CSGO中直接移植来的雷达图工作得很好！

![20230912190609_1.jpg](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/20230912190609_1.jpg)

我爱死这张第三人称了！

![20230912185905_1.jpg](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/20230912185905_1.jpg)

湖面波光粼粼，效果也很不错！

![20230912190632_1.jpg](https://raw.githubusercontent.com/obscurefreeman/devwikisource/main/docs/games/alienswarm/assets/20230912190632_1.jpg)



