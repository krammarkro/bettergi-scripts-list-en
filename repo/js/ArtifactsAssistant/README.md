
# Artifacts辅助

本脚本在后台定时运行，如果你在原神里面查看Inventory、Character身上的单个Artifacts，那么会在`BetterGI`的遮罩窗口显示文本，以告知这个Artifacts的评价、适用Character等等。

请先运行`overlay.exe`，它会不断读取`overlay.txt`并刷新到其窗口上，以解决`BetterGI`的遮罩窗口显示文本难以辨识的问题。

你也可以修改脚本自定义Configuration，`是否在遮罩窗口输出`取消勾选以避免在`BetterGI`的遮罩窗口显示信息。

输出信息Guide / Instructions：

``` txt
==== 完全Artifacts ====
Golden Troupe：生之花，金，等级+20
总点数：76.3，主属性：生命值 4780
副属性1：+0次，生命值+5.3%
副属性2：+0次，防御力+19
副属性3：+4次，暴击伤害+31.1%
副属性4：+1次，暴击率+7.4%
适配：Yae Miko、Chiori、Escoffier、Furina、Fischl、Albedo
词条点(61.1)：*暴击*、*暴伤*、攻击、精通
----------------
```

-   `==== 完全Artifacts ====`，表示五星初始四个词条而四星初始三词条，可能因计算误判
-   `==== Artifacts ====`，表示五星初始三个词条而四星初始两词条，这个不会误判
-   `总点数`，是Artifacts副属性所有点数之和，每个词条随机`7`到`10`点
-   `副属性`後接其已强化次数和属性值，`词条点`後接于Character适用词条的总点数和名称(有则带`*`)
-   `这个Artifacts不堪大用啊`，这个Artifacts对目前所有Character都不好用，可合成OtherArtifacts或当Artifact EXP喂掉
-   `适配：`，这个Artifacts可为Character的毕业Artifacts，如果属性点不好，可以考虑重塑一下
-   `可用：`，这个Artifacts可为Character的好用Artifacts，可以尝试看看属性点好不好


关于`Character一览.md`的Configuration：

1.  你可以自由修改或增加Configuration项，但必须符合原始语法
2.  数字序号後必须接空格和Character名称，例如`108. Durin`
3.  换行规则请务必Happy，不要缺少换行符，否则解析会出问题，请确保结尾有两个换行符
4.  一个搭配项的不同名称以`、`分隔，若Character有两种搭配，则每种搭配以`；`分隔，搭配项依次排列
5.  `Artifacts主词条：`Configuration`时之沙`、`空之杯`、`理之冠`的主属性，同一部件允许多个主属性则以`/`分隔
6.  六种默认模板`生命输出`,`攻击输出`,`防御输出`,`生命治疗`,`攻击治疗`,`防御治疗`，最好不要修改
