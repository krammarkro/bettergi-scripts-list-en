# BGI全Auto 地脉花脚本使用手册
**仅Supports BetterGI 0.63.2 及以上Version！**
**仅Supports Bitblt 截图方式！**
**仅Supports V4 OCR模型！**
目前脚本仍在更新，开发阶段会有很多bug，详见下方已知问题，如果遇到Nope提到的bug请反馈给我们，非常Thank You！
## 目录
- [Configuration](#Configuration)
  - [Configuration地图追踪策略和Combat策略](#Configuration地图追踪策略和Combat策略)
  - [Statue of The Seven](#Statue of The Seven)
- [特色介绍](#特色介绍)
- [FAQ](#FAQ)
  - [一运行就报错退出了](#一运行就报错退出了)
  - [找不到地脉花/找到地脉花，未找到策略](#找不到地脉花--找到地脉花未找到策略)
  - [走到地脉花旁边Nope开启地脉花](#走到地脉花旁边Nope开启地脉花)
  - [Route中途跳过了一个点位](#Route中途跳过了一个点位)
  - [跑完后大地图所有自定义的标点都没了](#跑完后大地图所有自定义的标点都没了)
- [Changelog](#Changelog)
- [Route](#Route)
  - [Mondstadt](#Mondstadt)
  - [Liyue](#Liyue)
  - [Inazuma](#Inazuma)
  - [Sumeru](#Sumeru)
  - [Fontaine](#Fontaine)
  - [Natlan](#Natlan)
  - [Nod-Krai](#Nod-Krai)
- [特别Thank You](#特别Thank You)
## Configuration
使用前需要对脚本以及Combat策略进行Configuration
在调度器新建一个Configuration组，将脚本添加进来，脚本只能在Configuration组内使用
![](assets/image/image1.png)
![](assets/image/image2.png)
![](assets/image/image3.png)
![](assets/image/image4.png)
右键脚本选择修改js脚本自定义Configuration，根据你的需要对脚本进行Configuration。
![](assets/image/image5.png)
### Configuration地图追踪策略和Combat策略
点击Configuration组Settings，开启Combat策略Configuration，**关闭Auto 检测Combat结束**，Other的根据你的队伍进行Configuration。
> 脚本不通过按L检查Combat是否结束，请务必关闭 **Auto 检测Combat结束** ，不关闭可能导致提前结束Combat!
> 也因此无法在Combat后进行拾取，Configuration与否均不会影响。
> Combat超时时间一定要大于或与脚本Configuration内的时间一样，太短会原地罚站！
> 脚本强制启用Auto 拾取，开关与否均不会影响。

![](assets/image/image6.png)
### Statue of The Seven
在bgiSettings内，**关闭就近Statue of The Seven**，指定一个Statue of The Seven，如无特殊要求Recommended选择SumeruAvidya Forest。  
如果您开启了All-in-One Run模式，将会跳过以节约时间。  
> 不要开启**传送到Statue of The Seven之后是否需要移动后回血**，目前这个FeaturesBug很多！

![](assets/image/image7.png)
### 开启 HTTP 权限
脚本需要开启 HTTP 权限检查是否有更新。  
在Configuration组内右键脚本，选择修改通用Configuration，将JS HTTP权限从**禁用**修改为**启用**。
![](assets/image/image9.png)
## 特色介绍
- **全Auto 运行**：Configuration好之后，只需要点击运行，就可以全部打完，无需任何Other操作。
- **Auto Searching地脉花**：通过大地图定位地脉花位置的方式来Searching地脉花，并执行后续的Route。
- **Auto 开启地脉花奖励，优先使用Condensed Resin**：领取奖励时优先选择Condensed Resin，当存在双倍奖励活动（地脉移涌或星之归还）时会优先选择双倍奖励。
- **双倍检测模式**：开启后仅在检测到双倍产出时才刷地脉，刷完后Auto 退出，适合只想用双倍活动的玩家。
- **材料拾取**：领奖后Auto 追踪拾取怪物掉落物，搭配20树脂模式可Efficient获取怪物素材（会触发短暂Combat）。
- **20树脂模式（怪物素材慢刷）**：每次仅消耗20体力，以效率换取更多怪物掉落素材机会，配合材料拾取效果更佳。
- **树脂耗尽模式**：根据Settings统计当前的树脂情况，计算出需要运行的次数，运行结束后再次判断，若结束后统计到未消耗的树脂则继续执行（最多3次）
- **树脂不足时Auto 停止**：如果领取奖励时树脂不够了，脚本会直接停止，可以Configuration是否使用须臾/脆弱。
- **Friendship队领取奖励**：领取奖励前Switch到Friendship队，还可以领取到Friendship度。
## FAQ
### 一运行就报错退出了
根据错误提示自行排查原因
### 找不到地脉花 / 找到地脉花，未找到策略
脚本还未适配，请等待脚本更新。
如果不是，请将出That's Wrong**完整游戏界面截图**反馈。
Note：为了方便截图反馈，出现该错误时不会关闭大地图界面！也不会将关闭的自定义标记按钮打开！
### 走到地脉花旁边Nope开启地脉花
- 请使用bitblt截图方式，脚本只Supports这个
- 请Switchocr引擎至v4，Other引擎脚本未进行适配
### Route中途跳过了一个点位
当地脉花打完后，下一个点位已经存在另一类型的地脉花，则下一朵地脉花将跳过这个点，刷新在下一个位置。
脚本会跳过这个被占用的点位。
![](assets/image/image8.png)
例如这里，Mora花刷新在经验花的下一个位置上。
### 跑完后大地图所有自定义的标点都没了
打开大地图，点击Bottom-Left角Settings，开启自定义标记。
脚本非正常结束运行时会出现该问题。
## Changelog
### 5.1
- 新增双倍检测模式（只刷双倍产出）
- 新增材料拾取Features（领奖后Auto 拾取掉落物）
- 新增20树脂模式（怪物素材慢刷，配合材料拾取使用）
- 修复Condensed Resin识别Defeat的问题
- 修复树脂耗尽模式+刷取次数取小值的情况下，当OCR计算次数>手动Settings刷取次数时无法正确终止脚本的bug（到达手动刷取次数会继续刷,直到体力用光）
### 5.0
- 新增SnezhnayaRoute
- BGI最低Version要求改为0.63.2
### 4.6
- 新增月之五VersionMondstadtRoute
### 4.5
- 新增月之四VersionNod-KraiRoute
### 4.4
- 新增树脂耗尽模式
- 新增树脂耗尽模式下刷取次数取小值
- 新增更新提醒
- 新增All-in-One Run模式
- BGI最低Version要求改为0.52.0
### 4.3
- 适配新的奖励领取界面
- 修复Nod-Krai识别错误及通过冒险之证Searching地脉花总会选择Nod-Krai的bug
- 修复卡在奖励领取界面无法执行OtherConfiguration的bug
- 优化冒险之征Searching地脉花的逻辑
- 新增是否使用须臾树脂Configuration选项
### 4.2
- 新增Nod-Krai区域
### 4.1
- 新增通过冒险之证Searching地脉花
- 修复部分报错
### 4.0
- 适配原神5.7Version更新
- 修复打开自定义标记的bug
### 3.5
- 减少部分Log输出
- 修改部分错误提示信息

### 3.4
- 重构代码结构
- 修复部分提示错误

### 3.3
- CombatDefeatRoute重试Supports
- 导航到地脉花优化

### 3.2
- 新增通知选项

### 3.1
- 新增Liyue、Sumeru部分Route
- 修改Searching地脉花领奖的逻辑

### 3.0
**本次更新内容很多，详情可以到[GitHub](https://github.com/babalae/bettergi-scripts-list/pull/633)上查看**
- 新增Route：Sal Terrae Yaoguang Shoal Yaodie Valley Tatarasuna Watatsumi Island Sulfurous Veins Tilted Branch Cliff Toyac Springs Yashiori Island Caishi Peak Flower-Feather Clan Narukami Island Seirai Island
Inazuma与Natlan的Route已全部补全
- 优化Combat相关逻辑，通过识别Challenge结果来判断Combat是否结束
- **全地脉花识别**
- 移除强制运行模式
- 优化地脉花Searching逻辑
- 优化地脉开启和领取奖励相关逻辑
- 新增优先使用双倍奖励（地脉移涌和星之归还）
### 2.1
- 重构Searching地脉花位置的方式为获取地脉花在游戏内的坐标
理论上会减少找不到地脉花的情况
- 新增 领取前可Switch至Friendship队（需Configuration）
### 2.0
- 新增 FontaineNew Fontaine Research Institute Lumidouce Harbor
至此，Fontaine全部Route已制作完成
- 修复 有Condensed Resin的情况下误认为树脂已用完
- 修复 无限重试
### 1.0
- 脚本发布

## Route
打钩的代表已制作完成
### Mondstadt
- [x] 1. Windrise

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Hilichurlx3<br>第二波：Hilichurlx1、Electro Hilichurl Shooterx2、Hydro Abyss Magex1
2 | 第一波：Large Electro Slimex1、Mutant Electro Slimex1、Electro Hilichurl Shooterx1<br>第二波：Large Electro Slimex1、Mutant Electro Slimex1、Hydro Samachurlx1、Cryo Hilichurl Shooterx2
3 | 第一波：Treasure Hoarders: Scoutx2、Treasure Hoarders: Gravediggerx1、Treasure Hoarders: Electro Potioneerx1<br>第二波：Treasure Hoarders: Marksmanx1、Treasure Hoarders: Handymanx1、Treasure Hoarders: Electro Potioneerx1、Treasure Hoarders: Crusherx1
4 | 第一波：Wooden Shield Hilichurl Guardx3、Hilichurl Grenadierx1、Pyro Slimex2<br>第二波：Hilichurl Berserkerx4
5 | 第一波：Large Hydro Slimex2、Cryo Whopperflowerx1<br>第二波：Electro Slimex3、Cryo Whopperflowerx1

- [x] 2. Springvale

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Large Pyro Slimex1、Electro Slimex2<br>第二波：Pyro Whopperflowerx1、Electro Slimex3
2 | 第一波：Large Pyro Slimex1、Pyro Slimex4<br>第二波：Pyro Whopperflowerx2
3 | 第一波：Pyro Hilichurl Shooterx2、Anemo Samachurlx1、Large Pyro Slimex1<br>第二波：Hilichurl Grenadierx2、Anemo Samachurlx1、Large Pyro Slimex1
4-1 | 第一波：Pyro Slimex2、Hilichurl Grenadierx2<br>第二波：Electro Hilichurl Shooterx3、Pyro Abyss Magex1
4-2/5-1 | 第一波：Eye of the Stormx1


- [x] 3. Wolvendom （特征点少，有概率Defeat）

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Treasure Hoarders: Scoutx3<br>第二波：Treasure Hoarders: Handymanx2、Treasure Hoarders: Marksmanx2
2 | 第一波：Ruin Guardx1
3 | 第一波：Pyro Hilichurl Shooterx2、Wooden Shield Hilichurl Guardx2<br>第二波：火斧Hilichurlx1、Anemo Samachurlx1、Hilichurl Grenadierx3
4 | 第一波：Wooden Shield Hilichurl Guardx2、Electro Hilichurl Shooterx2、Hilichurl Grenadierx2<br>第二波：Pyro Abyss Magex2

- [x] 4. Stormterror's Lair

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Treasure Hoarders: Scoutx2、Treasure Hoarders: Handymanx1、Treasure Hoarders: Marksmanx1<br>第二波：Treasure Hoarders: Scoutx2、Treasure Hoarders: Crusherx1、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Electro Potioneerx1
2 | 第一波：Ruin Hunterx1
3 | 第一波：Ruin Guardx1
4 | 第一波：Fatui Skirmisher - Electrohammer Vanguardx1、Fatui Skirmisher - Anemoboxer Vanguardx1<br>第二波：Fatui Skirmisher - Pyroslinger Bracerx2、愚人众先遣队·水锤重卫士x1

- [x] 5. Temple of the Thousand Winds

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Wooden Shield Hilichurl Guardx2、Electro Hilichurl Shooterx1、Cryo Hilichurl Shooterx1<br>第二波：Electro Hilichurl Shooterx1、Cryo Hilichurl Shooterx1、Hydro Samachurlx1、Wooden Shield Hilichurl Guardx1、Wooden Shieldwall Mitachurlx1
2 | 第一波：Wooden Shield Hilichurl Guardx2、Hilichurl Berserkerx2<br>第二波：Hilichurl Berserkerx3、Dendro Samachurlx1
3 | 第一波：Treasure Hoarders: Scoutx4、Treasure Hoarders: Marksmanx1<br>第二波：Treasure Hoarders: Pyro Potioneerx2、Treasure Hoarders: Pugilistx1、Treasure Hoarders: Crusherx1
4 | 第一波：Electro Slimex2、Hilichurl Berserkerx2、Wooden Shield Hilichurl Guardx1<br>第二波：Electro Slimex2、Hilichurl Grenadierx2、Blazing Axe Mitachurlx1
5 | 第一波：Wooden Shield Hilichurl Guardx2、Hilichurl Grenadierx2<br>第二波：Hilichurl Grenadierx2、Anemo Samachurlx1、Dendro Samachurlx1

- [x] 6. Stormbearer Mountains

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Large Cryo Slimex2、Large Hydro Slimex2<br>第二波：Cryo Hilichurl Shooterx2、Hydro Abyss Magex1
2 | 第一波：Hilichurl Grenadierx2、Anemo Samachurlx2<br>第二波：Electro Hilichurl Shooterx2、Hilichurl Grenadierx1、Blazing Axe Mitachurlx1
3 | 第一波：Pyro Whopperflowerx2<br>第二波：Electro Hilichurl Shooterx3、Pyro Abyss Magex1
4 | 第一波：Hilichurl Berserkerx3<br>第二波：Wooden Shieldwall Mitachurlx2、Hydro Samachurlx2

- [x] 7. Dadaupa Gorge

**地脉花总数：6**

顺序 | 怪物
--- | ---
1 | 第一波：Wooden Shield Hilichurl Guardx2、Hilichurl Shooterx2<br>第二波：Hydro Abyss Magex1、Cryo Hilichurl Shooterx2
2 | 第一波：Hilichurl Fighterx3、Hilichurl Grenadierx1<br>第二波：Hilichurl Berserkerx3、Blazing Axe Mitachurlx1
3 | 第一波：Hilichurl Fighterx2、Wooden Shield Hilichurl Guardx2、Pyro Hilichurl Shooterx1<br>第二波：Blazing Axe Mitachurlx2
4 | 第一波：Electro Hilichurl Shooterx2、Blazing Axe Mitachurlx1<br>第二波：Pyro Hilichurl Shooterx3、Dendro Samachurlx1
5 | 第一波：Wooden Shield Hilichurl Guardx2、Hydro Samachurlx1<br>第二波：Wooden Shield Hilichurl Guardx2、Electro Hilichurl Shooterx1、Hydro Abyss Magex1
6 | 第一波：Large Hydro Slimex2、Cryo Whopperflowerx1<br>第二波：Electro Slimex3、Cryo Whopperflowerx1

### Liyue
- [x] 1. Stone Gate

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Treasure Hoarders: Marksmanx2、Treasure Hoarders: Scoutx1、Treasure Hoarders: Crusherx1<br>第二波：Treasure Hoarders: Gravediggerx1、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Scoutx1、Treasure Hoarders: Marksmanx1
2 | 第一波：Large Geo Slimex1、Geo Slimex3<br>第二波：Large Geo Slimex2、Geo Slimex2
3 | 第一波：Pyro Abyss Magex1、Electro Hilichurl Shooterx2<br>第二波：火斧Hilichurl暴徒x1、Cryo Hilichurl Shooterx2、水Hilichurl萨满x1
4 | 第一波：Wooden Shieldwall Mitachurlx2<br>第二波：Rock Shieldwall Mitachurlx2
5 | 第一波：岩Hilichurl萨满x2、Hilichurl Grenadier投手x2<br>第二波：Rock Shield Hilichurl Guard暴徒x2

- [x] 2. Sal Terrae

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Hilichurl Berserkerx2、Hilichurl Grenadierx1、草Hilichurl萨满x1<br>第二波：Electro Hilichurl Shooterx2、Pyro Abyss Magex1
2 | 第一波：Hydro Cicinx3、Large Cryo Slimex1、Cryo Slimex1<br>第二波：雷Cicin Magex1
3 | 第一波：岩盔Lawachurlx1
4 | 第一波：Pyro Hilichurl Shooterx2、Hilichurl Berserkerx1、岩Hilichurl萨满x1<br>第二波：Electro Hilichurl Shooterx4、岩Hilichurl萨满x1

- [x] 3. Yaoguang Shoal

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Hydro Slimex2、Cryo Whopperflowerx1<br>第二波：Hydro Cicinx3、雷Cicin Magex1
2 | 第一波：Ruin Guardx1
3 | 第一波：Treasure Hoarder·拳术师x1、Treasure Hoarders: Marksmanx2、Treasure Hoarders: Pyro Potioneerx1<br>第二波：Treasure Hoarders: Scoutx1、Treasure Hoarders: Handymanx1、Treasure Hoarders: Marksmanx1、Treasure Hoarders: Seamanx1
4 | 第一波：Cryo Hilichurl Shooterx2、Electro Hilichurl Shooterx1<br>第二波：Cryo Abyss Magex1、Electro Hilichurl Shooterx1、水Hilichurl萨满x1
5 | 第一波：Large Pyro Slimex2、Pyro Slimex3<br>第二波：Pyro Whopperflowerx2


- [x] 4. Liyue Harbor

**地脉花总数：7**

顺序 | 怪物
--- | ---
1 | 第一波：Geovishap Hatchlingx2<br>第二波：Geovishap Hatchlingx2
2 | 第一波：岩盔Lawachurlx1
3 | 第一波：Fatui Skirmisher - Hydrogunner Legionnairex1、Fatui Skirmisher - Cryogunner Legionnairex1<br>第二波：Fatui Skirmisher - Anemoboxer Vanguardx1、Fatui Skirmisher - Electrohammer Vanguardx1
4 | 第一波：Large Geo Slimex1、Geo Slimex4<br>第二波：Large Geo Slimex3
5 | 第一波：Ruin Guardx1
6 | 第一波：Cryo Hilichurl Shooterx2、Electro Hilichurl Shooterx1<br>第二波：Cryo Abyss Magex1、Electro Hilichurl Shooterx1、水Hilichurl萨满x1
7 | 第一波：Large Pyro Slimex2、Pyro Slimex3<br>第二波：Pyro Whopperflowerx2

- [x] 5. Mt. Tianheng

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Ruin Hunterx1
2 | 第一波：Large Electro Slimex1、Mutant Electro Slimex1<br>第二波：Large Cryo Slimex1、Cryo Slimex3
3 | 第一波：Hydro Abyss Magex1、Cryo Slimex2<br>第二波：Cryo Abyss Magex1、Electro Hilichurl Shooterx2
分支Route1：|
4 | 第一波：Rock Shield Hilichurl Guardx4<br>第二波：Rock Shield Hilichurl Guard暴徒x2
分支Route2：|
4 | 第一波：Blazing Axe Mitachurlx2<br>第二波：Rock Shieldwall Mitachurlx1、Geo Samachurlx1、Hilichurl Grenadierx2
 
- [x] 6. Mt. Aocang

**地脉花总数：7/9**

顺序 | 怪物
--- | ---
1 | 第一波：Pyro Slimex3、Pyro Whopperflowerx1<br>第二波：Cryo Slimex3、Cryo Whopperflowerx1
2 | 第一波：Fatui Pyro Agentx1
3 | 第一波：Electro Slimex4、Pyro Whopperflowerx1<br>第二波：Large Geo Slimex2、Pyro Whopperflowerx1
4 | 第一波：Electro Slimex3、Hilichurl Berserkerx2、Rock Shield Hilichurl Guardx1<br>第二波：Pyro Slimex2、Hilichurl Grenadierx2、Rock Shield Hilichurl Guardx2
分支Route1：| 
5 | 第一波：Fatui Skirmisher - Electrohammer Vanguardx1、Fatui Skirmisher - Cryogunner Legionnairex1<br>第二波：Fatui Skirmisher - Electrohammer Vanguardx1、Fatui Skirmisher - Pyroslinger Bracerx1、Fatui Skirmisher - Geochanter Bracerx1
6 | 第一波：岩盔Lawachurlx1
7 | 第一波：雷Cicin Magex1、Electro Cicinx3
分支Route2：|
5 | 第一波：Electro Cicinx2、Fatui Pyro Agentx1
6 | 第一波：Rock Shield Hilichurl Guardx1、Pyro Hilichurl Shooterx3<br>第二波：火斧Hilichurl暴徒x1、Hilichurl Grenadier投手x2
7 | 第一波：Large Electro Slimex1、Electro Slimex3、Hydro Slimex2<br>第二波：Large Electro Slimex1、Mutant Electro Slimex1、Electro Slimex3、Large Hydro Slimex2
8 | 第一波：Large Cryo Slimex2<br>第二波：Large Hydro Slimex3
9 | 第一波：Large Pyro Slimex2、Pyro Slimex3<br>第二波：Pyro Whopperflowerx2

- [x] 7. Dunyu Ruins

**地脉花总数：7**

顺序 | 怪物
--- | ---
1 | 第一波：Electro Cicinx3、Hydro Cicinx3<br>第二波：雷Cicin Magex1
2 | 第一波：Treasure Hoarders: Electro Potioneerx1、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Marksmanx1、Treasure Hoarder·拳术师x1<br>第二波：Treasure Hoarder·拳术师x1、Treasure Hoarders: Handymanx1、Treasure Hoarders: Electro Potioneerx1、Treasure Hoarders: Pyro Potioneerx1
3 | 第一波：Large Cryo Slimex2<br>第二波：Cryo Whopperflowerx1、Large Hydro Slimex2
4 | 第一波：Pyro Abyss Magex1、Electro Hilichurl Shooterx2<br>第二波：Cryo Abyss Magex1、Electro Hilichurl Shooterx3
5 | 第一波：Large Cryo Slimex2<br>第二波：Large Hydro Slimex3
6 | 第一波：Large Pyro Slimex2、Pyro Slimex3<br>第二波：Pyro Whopperflowerx2

- [x] 8. Nantianmen南

**地脉花总数：7**

顺序 | 怪物
--- | ---
1 | 第一波：Ruin Guardx2
2 | 第一波：岩盔Lawachurlx1
3 | 第一波：火斧Hilichurl暴徒x2<br>第二波：Pyro Abyss Magex1、Hilichurl Berserkerx3
4 | 第一波：Large Electro Slimex1、Electro Slimex4<br>第二波：Pyro Whopperflowerx1、Electro Slimex4
5 | 第一波：Pyro Abyss Magex1、Electro Hilichurl Shooterx2<br>第二波：Cryo Abyss Magex1、Electro Hilichurl Shooterx3
6 | 第一波：Large Cryo Slimex2<br>第二波：Large Hydro Slimex3
7 | 植物：烈焰花x4<br>第一波：Large Pyro Slimex2、Pyro Slimex3<br>第二波：Pyro Whopperflowerx2

- [x] 9. Nantianmen东

**地脉花总数：2**

顺序 | 怪物
--- | ---
1 | 第一波：Pyro Whopperflowerx1、Pyro Slimex3<br>第二波：Geo Slimex4<br>第三波：Large Geo Slimex1、Geo Slimex2
2 | 第一波：Fatui Pyro Agentx1
分支Route1：| 
3 | 第一波：Treasure Hoarderx4<br>第二波：Treasure Hoarderx4
分支Route2：|
3 | 第一波：Ruin Hunterx1
4 | 第一波：火斧Hilichurl暴徒x1、Pyro Hilichurl Shooterx2<br>第二波：Anemo Samachurlx1、Electro Hilichurl Shooterx3

- [x] 10. Jueyun Karst

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Rock Shield Hilichurl Guardx4、Hilichurl Grenadier投手x1<br>第二波：水Hilichurl萨满x2、Cryo Abyss Magex1
2 | 第一波：Rock Shield Hilichurl Guardx1、Pyro Hilichurl Shooterx3<br>第二波：火斧Hilichurl暴徒x1、Hilichurl Grenadier投手x2
3 | 第一波：Large Electro Slimex1、Electro Slimex3、Hydro Slimex2<br>第二波：Large Electro Slimex1、Mutant Electro Slimex1、Electro Slimex3、Large Hydro Slimex2
4 | 第一波：Large Cryo Slimex2<br>第二波：Large Hydro Slimex3
5 | 第一波：Large Pyro Slimex2、Pyro Slimex3<br>第二波：Pyro Whopperflowerx2

- [x] 11. Qingce Village

**地脉花总数：6**

顺序 | 怪物
--- | ---
1 | 第一波：Large Cryo Slimex1、Large Hydro Slimex2<br>第二波：Large Electro Slimex1、Mutant Electro Slimex1、Large Pyro Slimex1
2 | 第一波：Treasure Hoarders: Marksmanx1、Treasure Hoarders: Handymanx1、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Scoutx1<br>第二波：Treasure Hoarders: Scoutx1、Treasure Hoarders: Gravediggerx1、Treasure Hoarders: Crusherx1
3 | 第一波：Rock Shield Hilichurl Guardx1、Electro Hilichurl Shooterx1、Cryo Hilichurl Shooterx2<br>第二波：Electro Hilichurl Shooterx2、Cryo Abyss Magex1
4 | 第一波：Fatui Skirmisher - Electrohammer Vanguardx1、Fatui Skirmisher - Cryogunner Legionnairex1<br>第二波：Fatui Skirmisher - Electrohammer Vanguardx1、Fatui Skirmisher - Pyroslinger Bracerx1、Fatui Skirmisher - Geochanter Bracerx1
5 | 第一波：岩盔Lawachurlx1
6 | 第一波：雷Cicin Magex1、Electro Cicinx3

- [ ] 12. Guyun Stone Forest（特征点少，录制困难）

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Large Cryo Slimex2、Cryo Slimex3<br>第二波：Cryo Whopperflowerx2
2 | 第一波：岩盔Lawachurlx1
3 | 第一波：Fatui Skirmisher - Hydrogunner Legionnairex1、Fatui Skirmisher - Cryogunner Legionnairex1、Fatui Skirmisher - Anemoboxer Vanguardx1<br>第二波：Fatui Pyro Agentx1
4 | 第一波：Hydro Abyss Magex1、Cryo Hilichurl Shooterx3<br>第二波：Cryo Abyss Magex1、Electro Hilichurl Shooterx2

- [x] 13. Mt. Xuanlian

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Hilichurlx3、Blazing Axe Mitachurlx1<br>第二波：Rock Shieldwall Mitachurlx2
2 | 第一波：Electro Slimex2、Large Electro Slimex2<br>第二波：Large Hydro Slimex2
3 | 第一波：Xuanwen Beastx2<br>第二波：Xuanwen Beastx2
4 | 第一波：Hilichurlx2、Rock Shield Hilichurl Guardx1、Hilichurl Berserkerx1、Hilichurl Grenadierx1<br>第二波：Blazing Axe Mitachurlx2

- [x] 14. Yaodie Valley

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Ruin Guardx2<br>第二波：Ruin Hunterx1
2 | 第一波：Xuanwen Beastx2<br>第二波：Xuanwen Beastx2
3 | 第一波：Hilichurlx3、Blazing Axe Mitachurlx1<br>第二波：Rock Shieldwall Mitachurlx2
4 | 第一波：Xuanwen Beastx2<br>第二波：Xuanwen Beastx2

### Inazuma
- [x] 1. Narukami Island

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Ruin Cruiserx2<br>第二波：Ruin Destroyerx2
2 | 第一波：Hydro Slimex5<br>第二波：Large Hydro Slimex2
3 | 第一波：Nobushi: Kikoubanx1、Nobushi: Hitsukebanx1、Nobushi: Jintoubanx1
4 | 第一波：Kairagi: Fiery Mightx1、Kairagi: Dancing Thunderx1

- [x] 2. Tatarasuna

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Fatui Electro Cicin Magex1、Mirror Maidenx1<br>第二波：Fatui Cryo Cicin Magex1、Mirror Maidenx1
2 | 第一波：Fatui Skirmisher - Geochanter Bracerx1、Fatui Skirmisher - Anemoboxer Vanguardx1<br>第二波：Fatui Pyro Agentx1、Mirror Maidenx1
3 | 第一波：Treasure Hoarders: Hydro Potioneerx2、Treasure Hoarders: Seamanx2<br>第二波：Treasure Hoarders: Gravediggerx1、Treasure Hoarders: Crusherx1
4 | 第一波：Ruin Scoutx1、Ruin Defenderx1<br>第二波：Ruin Destroyerx1、Ruin Cruiserx1
5 | 第一波：Kairagi: Dancing Thunderx1、Nobushi: Jintoubanx1、Treasure Hoarders: Cryo Potioneerx1、Treasure Hoarders: Hydro Potioneerx1<br>第二波：Kairagi: Dancing Thunderx1、Treasure Hoarders: Seamanx1

- [x] 3. Yashiori Island

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Kairagi: Fiery Mightx1、Kairagi: Dancing Thunderx1
2 | 第一波：Ruin Destroyerx3
3 | 第一波：Nobushi: Kikoubanx1、Nobushi: Hitsukebanx1、Nobushi: Jintoubanx1<br>第二波：Nobushi: Kikoubanx1、Nobushi: Hitsukebanx1、Nobushi: Jintoubanx1
4 | 第一波：Ruin Destroyerx3


- [x] 4. Watatsumi Island

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Electro Samachurlx1、Electro Hilichurl Grenadierx3<br>第二波：Electro Abyss Magex2
2 | 第一波：Anemo Specterx3、Large Anemo Slimex1<br>第二波：Hydro Specterx3、Large Hydro Slimex1
3 | 第一波：Nobushi: Hitsukebanx1、Nobushi: Jintoubanx2<br>第二波：Kairagi: Fiery Mightx1、Kairagi: Dancing Thunderx1
4 | 第一波：Fatui Skirmisher - Cryogunner Legionnairex1、Fatui Skirmisher - Hydrogunner Legionnairex1<br>第二波：Fatui Electro Cicin Magex1、Fatui Cryo Cicin Magex1
5 | 第一波：Fatui Skirmisher - Cryogunner Legionnairex1、Fatui Skirmisher - Electrohammer Vanguardx1<br>第二波：Fatui Skirmisher - Anemoboxer Vanguardx1、Fatui Skirmisher - Hydrogunner Legionnairex1、Fatui Skirmisher - Geochanter Bracerx1

- [x] 5. Seirai Island

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Electro Samachurlx1、Electro Hilichurl Grenadierx3<br>第二波：Electro Abyss Magex2
2 | 第一波：Anemo Specterx3、Large Anemo Slimex1<br>第二波：Hydro Specterx3、Large Hydro Slimex1
3 | 第一波：Nobushi: Hitsukebanx1、Nobushi: Jintoubanx2<br>第二波：Kairagi: Fiery Mightx1、Kairagi: Dancing Thunderx1
4 | 第一波：Fatui Skirmisher - Cryogunner Legionnairex1、Fatui Skirmisher - Hydrogunner Legionnairex1<br>第二波：Fatui Electro Cicin Magex1、Fatui Cryo Cicin Magex1
5 | 第一波：Fatui Skirmisher - Cryogunner Legionnairex1、Fatui Skirmisher - Electrohammer Vanguardx1<br>第二波：Fatui Skirmisher - Anemoboxer Vanguardx1、Fatui Skirmisher - Hydrogunner Legionnairex1、Fatui Skirmisher - Geochanter Bracerx1


### Sumeru
- [x] 1. Mawtiyima Forest

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Hydro Slimex2、Whirling Cryo Fungusx2<br>第二波：Winged Cryoshroomx1
2 | 第一波：Cryo Slimex4<br>第二波：Large Anemo Slimex2
3 | Ruin Drake: Skywatchx1
4 | 第一波：Eremite Crossbowx2、Eremite Linebreakerx1、Eremite Ravenbeak Halberdierx1<br>第二波：Eremite Crossbowx1、Eremite Axe Vanguardx1
5 | 第一波：Hilichurl Berserkerx2<br>第二波：Hilichurl Berserkerx2、Dendro Samachurlx1

- [x] 2. Port Ormos

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Winged Cryoshroomx1、Whirling Cryo Fungusx2、Stretchy Anemo Fungusx1<br>第二波：Grounded Hydroshroomx2
2 | 第一波：Winged Dendroshroomx1、Stretchy Pyro Fungusx2、Stretchy Geo Fungusx1<br>第二波：Winged Cryoshroomx2
3 | 第一波：Winged Dendroshroomx1、Floating Hydro Fungusx2、Whirling Electro Fungusx1<br>第二波：Winged Cryoshroomx2
4 | 第一波：Eremite Axe Vanguardx2、Eremite Linebreakerx1<br>第二波：Eremite Linebreakerx1、Eremite Sword-Dancerx1
5 | 第一波：Eremite Crossbowx1、Eremite Sword-Dancerx1、Eremite Ravenbeak Halberdierx1<br>第二波：Eremite Crossbowx2

- [x] 3. Pardis Dhyai

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Ruin Drake: Earthguardx1<br>第二波：Ruin Drake: Skywatchx1
2 | 第一波：Winged Cryoshroomx1、Floating Dendro Fungusx2<br>第二波：Winged Dendroshroomx1、Grounded Hydroshroomx1
3 | 第一波：Eremite Linebreakerx1、Eremite Axe Vanguardx1、Eremite Ravenbeak Halberdierx1<br>第二波：Eremite Crossbowx2、Eremite Linebreakerx1、Eremite Sword-Dancerx1
4 | 第一波：Stretchy Pyro Fungusx4<br>第二波：Large Pyro Slimex1、Stretchy Pyro Fungusx2、Whirling Electro Fungusx2

- [x] 4. Apam Woods

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Floating Hydro Fungusx3、Stretchy Anemo Fungusx1<br>第二波：Winged Cryoshroomx1
2 | 第一波：Floating Hydro Fungusx2、Floating Dendro Fungusx2<br>第二波：Winged Dendroshroomx1
3 | 第一波：Eremite Linebreakerx1、Eremite Crossbowx1、Eremite Ravenbeak Halberdierx1<br>第二波：Eremite Sword-Dancerx1、Eremite Axe Vanguardx1、Eremite Ravenbeak Halberdierx1
4 | 第一波：Eremite Daythunderx1<br>第二波：Eremite Sunfrostx1
5 | 第一波：Eremite Linebreakerx1、Eremite Crossbowx1、Eremite Axe Vanguardx1<br>第二波：Eremite Sword-Dancerx1、Eremite Ravenbeak Halberdierx1

- [x] 5. Aaru Village

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Eremite Crossbowx1、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Marksmanx1<br>第二波：Eremite Ravenbeak Halberdierx1、Eremite Axe Vanguardx1、Treasure Hoarders: Marksmanx1
2 | 第一波：Stretchy Electro Fungusx1、Whirling Electro Fungusx1、Stretchy Geo Fungusx1<br>第二波：Grounded Geoshroomx1、Stretchy Anemo Fungusx1
3 | 第一波：Eremite Linebreakerx1、Eremite Sword-Dancerx1、Eremite Axe Vanguardx1、Eremite Crossbowx1<br>第二波：Eremite Sunfrostx1、Eremite Ravenbeak Halberdierx1
4 | 第一波：Stretchy Pyro Fungusx1、Stretchy Geo Fungusx1、Whirling Pyro Fungusx1<br>第二波：Grounded Geoshroomx2、Stretchy Geo Fungusx1
5 | 第一波：Eremite Desert Clearwaterx1<br>第二波：Eremite Daythunderx1、Eremite Sunfrostx1

- [x] 6. Valley of Dahri

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Whirling Pyro Fungusx2、Whirling Electro Fungusx2<br>第二波：Grounded Geoshroomx1、Whirling Pyro Fungusx2
2 | 第一波：Eremite Ravenbeak Halberdierx2、Eremite Axe Vanguardx1<br>第二波：Eremite Sunfrostx1、Treasure Hoarders: Pyro Potioneerx1
3 | 第一波：Eremite Sword-Dancerx1、Eremite Ravenbeak Halberdierx1、Eremite Linebreakerx1<br>第二波：Eremite Daythunderx1、Eremite Ravenbeak Halberdierx2
4 | 第一波：Eremite Axe Vanguardx1、Eremite Ravenbeak Halberdierx1、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Electro Potioneerx1<br>第二波：Eremite Desert Clearwaterx1、Eremite Crossbowx2

- [ ] 7. The Mausoleum of King Deshret （特征点少，录制困难）

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：Fatui Pyro Agentx1、愚人众·岩使游击兵x1、愚人众·火铳游击兵x1<br>第二波：愚人众·雷锤前锋军x1、愚人众·风拳前锋军x1
2 | 第一波：Stretchy Geo Fungusx3、Stretchy Pyro Fungusx1<br>第二波：Grounded Geoshroomx1、Whirling Pyro Fungusx2
3 | 第一波：Primal Construct: Repulsorx1<br>第二波：Primal Construct: Prospectorx1
4 | 第一波：Eremite Linebreakerx1、Eremite Ravenbeak Halberdierx1、Eremite Crossbowx1、Eremite Axe Vanguardx1<br>第二波：Eremite Galehunterx1
5 | 第一波：Eremite Stone Enchanterx1、Eremite Daythunderx1<br>第二波：Eremite Galehunterx1、Eremite Desert Clearwaterx1

- [x] 8. Wounded Shin Valley

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Grounded Geoshroomx1、Stretchy Geo Fungusx1<br>第二波：Winged Dendroshroomx1、Floating Dendro Fungusx1
2 | 第一波：Primal Construct: Prospectorx1<br>第二波：Primal Construct: Reshaperx1、Primal Construct: Repulsorx1
3 | 第一波：Eremite Desert Clearwaterx1、Eremite Daythunderx1<br>第二波：Eremite Sunfrostx1、Eremite Scorching Loremasterx1
4 | 第一波：Flying Serpentx3<br>第二波：Flying Serpentx1、Consecrated Flying Serpentx1

- [x] 9. Steel Dunes

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Primal Construct: Repulsorx1<br>第二波：Primal Construct: Reshaperx1、Primal Construct: Prospectorx1
2 | 第一波：Ruin Drake: Earthguard<br>第二波：Ruin Drake: Skywatch
3 | 第一波：Grounded Geoshroomx1、Whirling Pyro Fungusx1<br>第二波：Grounded Hydroshroomx1、Floating Anemo Fungusx1、Floating Dendro Fungusx1
4 | 第一波：Eremite Galehunterx1<br>第二波：Eremite Sunfrostx1、Eremite Floral Ring-Dancerx1

- [x] 10. Tunigi Hollow

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | Consecrated Scorpionx1
2 | Eremite Scorching Loremasterx1
3 | 第一波：Anemo Hilichurl Roguex1、Pyro Hilichurl Shooterx2、Hydro Samachurlx1<br>第二波：Hydro Hilichurl Roguex1、Blazing Axe Mitachurlx1
4 | Consecrated Red Vulturex1



### Fontaine
- [x] 1. ‍West Slopes of Mont Automnequi

**地脉花总数：5**

顺序 | 怪物
--- | ---
1 | 第一波：机关•侦察Recording型（荒）x4<br>第二波：Suppression Specialist Mek（荒）x2
2 | 第一波：机关•地质勘探型（荒）x2、机关•灵活采集型（荒）x2<br>第二波：Assault Specialist Mek（荒）x2
3 | 第一波：Treasure Hoarder•杂工x1、Treasure Hoarder•海上男儿x1、Treasure Hoarder•斥候x2<br>第二波：Treasure Hoarder•火之药剂师x2、Treasure Hoarder•雷之药剂师x1
4 | 第一波：Sternshield Crabx1、Armored Crabx3<br>第二波：Sternshield Crabx2
5 | 第一波：Tainted Water-Splitting Phantasmx2<br>第二波：Tainted Water-Splitting Phantasmx1、Tainted Water-Spouting Phantasmx2

- [x] 2. ‍芒索斯山东麓

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：侦察Recording型·荒x1，压制特化型·荒（火）x1<br>第二波：侦察Recording型·荒x1，歼灭特化型·荒（水）x1
2 | 第一波：风拳x1，霜役人x1<br>第二波：火枪x1，Wind Operativex1
3 | 第一波：算力增幅器·芒x1，建造特化型·芒（火）x1<br>第二波：算力增幅器·芒x1，攻坚特化型·芒（火）x1
4 | 第一波：火枪x1，雷莹x1<br>第二波：Wind Operativex1，霜役人x1

- [x] 3. ‍New Fontaine Research Institute

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：灵活采集型·荒x2，压制特化型·荒（火）x1<br>第二波：攻坚特化型·荒（雷）x1
2 | 第一波：地质勘探型·芒x2，歼灭特化型·芒（雷）x1<br>第二波：歼灭特化型·芒（雷）x1
3 | 第一波：歼灭特化型·芒（雷）x1，压制特化型·芒（草）x1<br>第二波：歼灭特化型·芒（雷）x1
4 | 第一波：算力增幅型·荒x1，侦察Recording型·荒x2<br>第二波：建造特化型·荒（冰）x1，灵活采集型·荒x1

- [x] 4. ‍Lumidouce Harbor

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Tainted Water-Splitting Phantasmx2<br>第二波：Tainted Water-Splitting Phantasmx2
2 | 第一波：Tainted Water-Spouting Phantasmx2<br>第二波：Tainted Water-Spouting Phantasmx2
3 | 第一波：Armored Crabx5<br>第二波：Sternshield Crabx2
4 | 第一波：Cherubic Sea Harex2<br>第二波： Cherubic Sea Harex2

- [x] 5. ‍East Slopes of Mont Automnequi

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Wind Operativex1，霜役人x1<br>第二波：Wind Operativex1，霜役人x1
2 | 第一波：侦察Recording型·芒x3<br>第二波：灵活采集型·芒x2
3 | 第一波：地质勘探型·芒x2<br>第二波：歼灭特化型·芒（雷）x2
4 | 第一波：灵活采集型·荒x2<br>第二波：攻坚特化型·荒（雷）x2

- [x] 6. ‍Elynas

**地脉花总数：6**

顺序 | 怪物
--- | ---
1 | 第一波：Blazing Axe Mitachurlx1、Hilichurl Fighterx2<br>第二波：Anemo Hilichurl Roguex1、Electro Samachurlx1、
2 | 第一波：机关•地质勘探型x2<br>第二波：Construction Specialist Mekx1、机关•灵活采集型x1
3 | 第一波：Sternshield Crabx1、Armored Crab（红）x2、Armored Crab（绿）x1<br>第二波：Sternshield Crabx2
4 | 第一波：Tainted Water-Splitting Phantasmx2<br>第二波：Tainted Water-Splitting Phantasmx2
5 | 第一波：Treasure Hoarder•海上男儿x1、Treasure Hoarder•斥候x2、Treasure Hoarder•雷之药剂师x1<br>第二波：Treasure Hoarder•掘墓者x1、Treasure Hoarder•海上男儿x1
6 | 第一波：Assault Specialist Mekx1、机关•侦察Recording型x1<br>第二波：Annihilation Specialist Mekx1、机关•侦察Recording型x1

### Natlan
- [x] 1. Huitztli Hill

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Forged Sand Interrogatorx1、Forged Sand Shieldbreakerx3、Tepetlisaur Whelpx1<br>第二波：Tepetlisaurus Warrior: Shard Strikerx1、Tepetlisaurus Warrior: Rockbreaker Bladex1
2 | 第一波：Treasure Hoarders: Scoutx1、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Hydro Potioneerx1<br>第二波：Treasure Hoarders: Scoutx3、Treasure Hoarders: Pyro Potioneerx1、Treasure Hoarders: Hydro Potioneerx1
3 | 第一波：Yumkasaur Whelpx2、疾讯勇士·引索客x1、疾讯勇士·荡风斥候x1<br>第二波：Yumkasaurus Warrior: Whirling Leavesx2
4 | 第一波：Forged Sand Interrogatorx3、Forged Sand Shieldbreakerx1、Forged Sand Javelineerx1<br>第二波：Tepetlisaurus Warrior: Shard Strikerx1、Tepetlisaurus Warrior: Rockbreaker Bladex1


- [x] 2. Sulfurous Veins

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Yumkasaur Whelpx1、疾讯勇士·荡风斥候x1、疾讯勇士·重刃讯使x1、Yumkasaurus Warrior: Flowing Skyfirex1<br>第二波：疾讯勇士·引索客x1、Yumkasaurus Warrior: Whirling Leavesx1
2 | 第一波：疾讯勇士·引索客x3、Yumkasaur Whelpx2<br>第二波：Yumkasaurus Warrior: Flowing Skyfirex1、Yumkasaurus Warrior: Whirling Leavesx1
3 | 第一波：Fatui Skirmisher - Pyroslinger Bracerx1、Fatui Skirmisher - Electrohammer Vanguardx1<br>第二波：Fatui Skirmisher - Pyroslinger Bracerx1、Fatui Skirmisher - Electrohammer Vanguardx1、Fatui Skirmisher - Cryogunner Legionnairex1
4 | 第一波：Yumkasaur Whelpx2、疾讯勇士·引索客x1、疾讯勇士·荡风斥候x1<br>第二波：Yumkasaurus Warrior: Whirling Leavesx1、Yumkasaurus Warrior: Flowing Skyfirex1

- [x] 3. Caishi Peak

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Eroding Avatar of Lavax2<br>第二波：Eroding Avatar of Lavax2
2 | 第一波：Tepetlisaur Whelpx1、Tepetlisaurusx1、Forged Sand Javelineerx1<br>第二波：Tepetlisaurusx2、Forged Sand Shieldbreakerx1、Forged Sand Interrogatorx1
3 | 第一波：Yumkasaur Whelpx1、Yumkasaurusx1、Yumkasaurus Warrior: Flowing Skyfirex1<br>第二波：Yumkasaur Whelpx1、Yumkasaurusx2、疾讯勇士·引索客x1
4 | 第一波：Tepetlisaur Whelpx2、Forged Sand Javelineerx1、Tepetlisaurus Warrior: Rockbreaker Bladex1<br>第二波：Tepetlisaur Whelpx3、Tepetlisaurusx2、Tepetlisaurus Warrior: Shard Strikerx1

- [x] 4. Toyac Springs

**地脉花总数：2**

顺序 | 怪物
--- | ---
1 | 第一波：Koholasaur Whelpx3、Flowing Blade Skirmisherx2<br>第二波：Koholasaurus Warrior: Waveshuttlerx1、Koholasaurus Warrior: Reefsplitterx1
2 | 第一波：Flowing Blade Skirmisherx1、Flowing Blade Grease-Sawx1、Flowing Blade Harpoon-Throwerx2<br>第二波：Koholasaurus Warrior: Waveshuttlerx1、Koholasaurus Warrior: Reefsplitterx1

- [x] 5. Atocpan

**地脉花总数：2**

顺序 | 怪物
--- | ---
1 | 第一波：Tatankasaur Whelpx4、Ferocious Warrior: Human Ramx1<br>第二波：Tatankasaur Whelpx2、Tatankasaurusx2、Ferocious Warrior: Grapplerx1
2 | Furnace Shell Mountain Weaselx1
3 | 第一波：Tatankasaur Whelpx3、Tatankasaurusx1、Ferocious Warrior: Human Ramx1<br>第二波：Tatankasaur Whelpx3、Tatankasaurusx2

- [x] 6. Stadium of the Sacred Flame

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Secret Source Automaton: Hunter-Seekerx1<br>第二波：Secret Source Automaton: Hunter-Seekerx1
2 | 第一波：Yumkasaur Whelpx1、Yumkasaurusx1、疾讯勇士·重刃讯使x1、Yumkasaurus Warrior: Whirling Leavesx1<br>第二波：Yumkasaur Whelpx2、Yumkasaurusx1、疾讯勇士·重刃讯使x1
3 | 第一波：Yumkasaur Whelpx2、疾讯勇士·引索客x1、Yumkasaurus Warrior: Flowing Skyfirex1<br>第二波：Yumkasaur Whelpx2、Yumkasaurusx1、Yumkasaurus Warrior: Whirling Leavesx1
4 | 第一波：Yumkasaur Whelpx2、Yumkasaurusx1、Yumkasaurus Warrior: Whirling Leavesx1<br>第二波：Yumkasaur Whelpx1、Yumkasaurusx2、Yumkasaurus Warrior: Whirling Leavesx1

- [x] 7. Masters of the Night-Wind

**地脉花总数：3**

顺序 | 怪物
--- | ---
1 | 第一波：Spiritspeaker Warrior: Contemplatorx1、Spiritspeaker Warrior: Determinatorx1、Iktomisaurus Chickx1<br>第二波：Spiritspeaker Warrior: Contemplatorx1、Spiritspeaker Warrior: Determinatorx1、Iktomisaurus Chickx1、Iktomisaurus Warrior: Cryocrystal Cannonx1
2 | 第一波：Spiritspeaker Warrior: Contemplatorx1、Spiritspeaker Warrior: Psychokineticx1、Iktomisaurus Chickx1<br>第二波：Spiritspeaker Warrior: Contemplatorx3、Iktomisaurus Warrior: Cryocrystal Cannonx1
3 | 第一波：Secret Source Automaton: Hunter-Seekerx1

- [x] 8. Flower-Feather Clan

**地脉花总数：3**

顺序 | 怪物
--- | ---
1 | 第一波：焚然·Wayob Manifestationx1
2 | 第一波：Qucusaurus Chickx2、Winged Warrior: Feathershedderx1、Winged Warrior: Skysoarerx1<br>第二波：Qucusaurus Chickx1、Winged Warrior: Skysoarerx1、Winged Warrior: Skymasterx1、Qucusaurus Warrior: Heartstar Hammerx1
3 | 第一波：Qucusaurus Chickx1、Winged Warrior: Skymasterx1、Qucusaurus Warrior: Blazing Skyx1<br>第二波：Qucusaurus Chickx1、Winged Warrior: Skymasterx1、Winged Warrior: Feathershedderx1、Winged Warrior: Skysoarerx1、Qucusaurus Warrior: Blazing Skyx1

- [x] 9. Tilted Branch Cliff

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Koholasaur Whelpx3、Koholasaurusx1、Flowing Blade Skirmisherx1<br>第二波：Koholasaur Whelpx1、Koholasaurusx2、Flowing Blade Skirmisherx1
2 | 第一波：Qucusaurus Chickx3、Qucusaurusx1、Winged Warrior: Skymasterx1<br>第二波：Qucusaurus Chickx2、Qucusaurusx2、Winged Warrior: Skymasterx1
3 | 第一波：Koholasaur Whelpx3、Koholasaurusx1、Flowing Blade Grease-Sawx1<br>第二波：Koholasaur Whelpx2、Koholasaurusx2、Flowing Blade Skirmisherx1
4 | 第一波：深邃拟态·Tepetlisaurusx1、深邃拟态·Yumkasaurusx1、深邃拟态·Koholasaurusx1<br>第二波：深邃拟态·Tepetlisaurusx1、深邃拟态·Yumkasaurusx1、深邃拟态·Koholasaurusx1

- [x] 10. Toyac Springs

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Koholasaur Whelpx3、Koholasaurusx1、Koholasaurus Warrior: Reefsplitterx1<br>第二波：Koholasaur Whelpx2、Koholasaurusx2、Koholasaurus Warrior: Waveshuttlerx1
2 | 第一波：Flow-Inverted Wayob Manifestation<br>第二波：Flow-Inverted Wayob Manifestation
3 | 第一波：Koholasaur Whelpx3、Koholasaurusx1、Flowing Blade Harpoon-Throwerx1、Flowing Blade Skirmisherx1<br>第二波：Koholasaurusx2、Flowing Blade Harpoon-Throwerx1、Koholasaurus Warrior: Reefsplitterx1
4 | 第一波：Koholasaur Whelpx3、Koholasaurusx1、Koholasaurus Warrior: Waveshuttlerx1<br>第二波：Koholasaur Whelpx2、Koholasaurusx1、Flowing Blade Harpoon-Throwerx1、Flowing Blade Skirmisherx1

- [x] 11. 呼呼丘

**地脉花总数：3**

顺序 | 怪物
--- | ---
1 | 第一波：Tatankasaurus×2、Tatankasaur Whelpx1、Flowing Blade Harpoon-Throwerx1<br>第二波：Tatankasaurus×2、Tatankasaur Whelpx1、Tatankasaurus Warrior: Skybreaker×1
2 | 第一波：Foliar-Swift Wayob Manifestation<br>第二波：Foliar-Swift Wayob Manifestation
3 | 第一波：Qucusaurus Chickx3、Qucusaurusx1、Winged Warrior: Skymasterx1<br>第二波：Qucusaurus Chickx1、Qucusaurusx2、Winged Warrior: Feathershedderx1、Winged Warrior: Skysoarerx1

- [x] 12. Wavey Bay

**地脉花总数：3**

顺序 | 怪物
--- | ---
1 | 第一波：幼瞑视龙x1、瞑视龙x2、Spiritspeaker Warrior: Contemplatorx1<br>第二波：幼瞑视龙x2、瞑视龙x2、Spiritspeaker Warrior: Contemplatorx1
2 | 第一波：Tepetlisaur Whelpx1、Tepetlisaurusx1、Forged Sand Interrogatorx1、Forged Sand Javelineerx1<br>第二波：：Tepetlisaur Whelpx1、Tepetlisaurusx2、Tepetlisaurus Warrior: Shard Strikerx1
3 | 第一波：Secret Source Automaton: Hunter-Seekerx1<br>第二波：Secret Source Automaton: Hunter-Seekerx1

### Nod-Krai
- [x] 1. ‍Mossbone Wastes

**地脉花总数：2**

顺序 | 怪物
--- | ---
1 | 第一波：<br>第二波：
2 | 第一波：<br>第二波：

- [x] 2. ‍蓝泊湖

**地脉花总数：2**

顺序 | 怪物
--- | ---
1 | 第一波：<br>第二波：
2 | 第一波：<br>第二波：

- [x] 3. ‍Hiisi Island

**地脉花总数：4**

顺序 | 怪物
--- | ---
1 | 第一波：Gleaming Charge: Frostnight Scion×1<br>第二波：Gleaming Charge: Frostnight Scion×1
2 | 第一波：Oprichniki Vanguard×2、愚人众特辖队·愈疗师×1、Close Combat Scout Landcruiser×1<br>第二波：???×1、Oprichniki Vanguard×2、Force Recon Scout Landcruiser×1
3 | 第一波：Wilderness Exile×3<br>第二波：Wilderness Exile×2、Wilderness Hunter×1
4 | 第一波：Oprichniki Grenadier×2、Oprichniki Vanguard×1、愚人众特辖队·愈疗师×1<br>第二波：???×2、Oprichniki Hailstorm Cannoneer×1、Force Recon Storm Landcruiser×1

- [x] 4. ‍Kuuvahki Experimental Design Bureau

**地脉花总数：3**

顺序 | 怪物
--- | ---
1 | 第一波：Oprichniki Line Trooper×2、Close Combat Scout Landcruiser×2<br>第二波：Close Combat Scout Landcruiser×1、Oprichniki Support Trooper×1、Oprichniki Hailstorm Cannoneer×1
2 | 第一波：Oprichniki Support Trooper×1、Close Combat Storm Landcruiser×1、Force Recon Storm Landcruiser×1<br>第二波：Oprichniki Line Trooper×1、Force Recon Storm Landcruiser×1、Oprichniki Fireblade Shock Trooper×1
3 | 第一波：Radiant Bladehorn×1<br>第二波：Radiant Bladehorn×1

## 特别Thank You
- Thank You 平面镜 制作的Fontaine地脉花脚本，~~抄了很多代码，~~以及FontaineRoute！
- Thank You 秋云 在脚本制作期间提供了很多Features实现的思路，开放了很多非常方便的方法，并修改优化了大量代码，这个脚本说是他写的也不为过！
- Thank You 起个名字好难的喵 协助脚本的开发，帮大忙了！
- Thank You v7群群友 在正式发布前对脚本进行测试！~~虽然没Roger That几个反馈~~
- Thank You 测试群群友 Help制作了部分Route，提供用于制作Route的Account以及对脚本的测试！~~合格黑奴~~
- Thank You 辉鸭蛋 制作的BetterGI！