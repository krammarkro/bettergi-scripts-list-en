# AAA Artifact EXP批发

## 琪零、Features及部分原理Guide / Instructions
1. 根据时间Auto 选择卡时间和Route，方案具体参考下列Guide / Instructions：
- 两条NormalRoute全富点98交替执行
- 达到预期激活时间后（比昨天晚1分钟）先去激活以固定刷新时间，如果NormalRoute执行完成仍然未达到目标时间，则启用AlternateCleanupRoute（昨天跑**AlternateCleanupRoute**时第二天可直接跑收益更高的**优先CleanupRoute**），Snezhnaya玻璃罐只在Cleanup额外A中会被激活。
- 激活完成后继续跑剩余的NormalRoute（激活时不会拾取，原理见[Investigating点机制](#Investigating点机制与刷新cd)。**如果你什么都没看就直接问为什么不捡**，那我将视其为狗叫并对你进行狠狠的进攻！）
- 最后按顺序跑Cleanup和额外Route
2. Supports多样化的分解Artifact EXPConfiguration，具体参考自定义Configuration和下面的Guide / Instructions
3. Supports断点续跑，中断后一天之内重跑将会Auto 跳过已运行的Route，执行应该执行的Route，但是仍然不建议在激活Route期间（约3分钟）中断
4. Auto 识别运行Defeat的Route并在Log中进行Warning，建议尽快手动Go to开图

## 芽一、Usage及Configuration

1. 将脚本添加至调度器。
2. 右键点击脚本以修改 JS 自定义Configuration。
- **请输入Artifact EXP队伍名称**：改成自己捡Artifact EXP的队伍名字。建议使用迪西雅或e启动奶妈作为行走位，如果需要Configuration生存位，建议与行走位相同。建议携带：迪西雅（耐肘王，提供移速加成），Kaedehara Kazuha（Route中有ConfigurationKaedehara Kazuha吸取Artifact EXP，可提高拾取率）。
- **请输入清怪队伍名称**：改成自己的Combat队，清理Artifact EXPRoute上的Common Mobs，不填则跳过清怪Route，**需要自行匹配Combat策略。**
- **最短时间间隔**：比昨天延后（默认1分钟）Starting Up卡Cleanup点和额外点。
- **最大额外等待时间**：98个点拾取完后，可以选择干等N分钟来卡更多次的超限点，当Auto 延时累计超过(30+最大额外等待时间)分钟Auto 重置激活和额外A（每日Auto 延时+1分钟默认），重置时Skip激活和额外A。
- **强制CleanupRoute交替执行**：默认不开，用于一些用户想收集Other的Investigating材料，比如茶叶等。替换掉（替补CleanupRoute）内的文件，可以一天CleanupArtifact EXP，一天Cleanup茶叶。
- **SnezhnayaRoute激活Configuration**：默认关闭，启用后执行Route激活操作不拾取Artifact EXP，开启时定时激活Route方便后续跑罐罐联机。
- **Snezhnaya额外CleanupRoute**：默认关闭，启用后执行Snezhnaya额外Route拾取Artifact EXP，给只想捡自己世界的玩家开启，联机互刷玩家不要开启。
- **Artifact EXP分解模式**：默认不分解，可选分解成（经验瓶/Mora）。
- **账户名称**：**单Account无需更改。** 多Account使用时建多个Configuration组，一个Account使用一个Configuration组，填入游戏Account名称（自己取名），就可以按各自名称分别Recording运行信息。
- **Furina**：Artifact EXP队SupportsAuto 使用白芙作为生存位（汐姐姐逼的，非必要不要用，会慢很多），当你Artifact EXP队伍中一定要含有Furina时勾选，将确保Artifact EXPRoute时Furina为白芙状态，清怪和脚本结束时切回黑芙。

## 二、FastStarting Up

首次使用建议先采用以下最小Configuration：

- Artifact EXP队伍名称：填写 BetterGI 中实际使用的队伍名称
- 清怪队伍名称：不需要清怪时留空
- 最短时间间隔：`1`
- 最大额外等待时间：`0`
- CleanupRoute：不勾选“联机Cleanup模式”
- 急速模式：不勾选
- Artifact EXP分解模式：`保留`
- 拾取模式：`模板匹配拾取`

RecommendedConfiguration：

| 模式 | 适用场景 | 关键Configuration |
|---|---|---|
| Stable模式 | 首次使用、电脑性能一般 | 急速模式关闭；分解模式为保留；拾取模式为模板匹配拾取；最大额外等待为0 |
| 急速模式 | 只追求较短运行时间，可接受收益下降 | 开启急速模式；不执行激活和准备Route；使用高铁Route |
| 联机模式 | 为联机Cleanup准备Investigating点 | 开启联机Cleanup模式；填写 `autoOnline`；按需Configuration清怪队伍；建议使用 bgi 原版拾取 |

### 运行前提

- 使用Supports本脚本 API 的 BetterGI Version；当前Route元数据要求 `bgi_version 0.45.0`，并确保地图追踪Features正常。
- 游戏画面使用 `1920×1080` 分辨率；脚本中的识别区域和点击坐标按此分辨率Configuration。
- 游戏按键保持默认Settings，尤其是Investigating/拾取使用的 `F` 键。
- Artifact EXP队伍名称必须与 BetterGI Configuration中的名称完全一致。
- 填写清怪队伍时，必须为该队伍Configuration对应的Combat策略；留空则跳过清怪Route。
- 使用 `bgi原版拾取` 时，需要在 BetterGI 中启用并正确Configuration `AutoPick`。
- 使用Furina选项时，Artifact EXP队伍必须包含Furina；否则不要勾选。
- 使用联机模式和 `autoOnline` 时，需要配合Supports对应命令格式的外部工具。

### Configuration格式限制

- 账户名称用于生成Recording文件，不能包含 `\\ / : * ? " < > |`，不能以空格开头或结尾，不能使用 Windows 保留设备名，长度不能超过 255 个字符。
- 最短时间间隔和最大额外等待时间填写非负整数，单位为分钟。
- `TMthreshold` 填写 0 到 1 之间的小数；误捡时调高，漏捡时调低。
- `findFInterval` 单位为毫秒，脚本会将其限制在 16 到 200 毫秒之间。
- `autoOnline` 格式为 `游戏名称-UID-目标房间`，名称和房间名中不要使用短横线 `-`。
- 只有在开启联机Cleanup模式时才填写 `autoOnline`；Normal模式留空即可。

## 三、运行原理

### Investigating点类型收益

| 类型 | 等效1星Artifacts | 平均经验值 | 平均Mora | 计算公式 |
|---|---|---|---|---|
| 穷点 | 1.35个        | 567 EXP    | 0        | 65%出1星(420EXP)+35%出2星(840EXP)  |
| 富点 | 1.5个         | 630 EXP    | 200      | 50%出1个1星(420EXP)/2个1星(840EXP) |


### Investigating点机制与刷新CD

#### 误区

❌ *错误认知*：很多人误以为Investigating点的 **24小时CD** 是从 **按FInvestigating** 时Starting Up计算的。

#### 实际机制

✅ **核心原理**：
- **游戏程序只会加载以玩家为圆心，固定半径内地图资源，Investigating点也在此时被激活，产生发光特效（CD倒计时未结束不会被激活）即数据出现在内存中时CD倒计时Auto Starting Up。**
- **每天4点刷新可互动的Investigating点上限100个，Investigating满上限后，进入未加载区域，Investigating点将不再被激活。** 在最后范围内，已经激活的Investigating点不会消失，可以继续Investigating。

#### 重要特性

- **与是否Investigating/拾取无关**！即使不Investigating或下线，CD仍会继续倒计时。例：今天你10点路过某区域，24小时CD的Investigating点Starting Up发光随后离开，15点再回来拾取Investigating点。明天此Investigating点会在10点CD倒计时结束，可以再次拾取。
- **单日多次加载无效**：若在CD未结束前重复加载Investigating点（无论拾取与否），都不会重置计时。


### RouteConfiguration与收益

#### 主要Route参数

| Route名称 | Investigating点 | 富点数量 | 穷点数量 | 总经验值 | 总Mora | 运行时间 | 98上限点富% |
|---|---|---|---|---|---|---|---|
| 富ARoute  | 162    | 105      | 57       | 99,099   | 22,600 | 69分钟   | 98/98 (100%)  |
| 富BRoute  | 135    | 105      | 30       | 83,790   | 21,000 | 53分钟   | 98/98 (100%)  |
| ABE A线  | 137    | 33       | 104      | 77,742   | 6,600  | 41分钟   | 27/98 (27.5%) |
| ABE B线  | 138    | 34       | 104      | 77,868   | 6,800  | 43分钟   | 33/98 (33.6%) |
| Snezhnaya额外  | 34    | 34      | 0       | 20400   | 5100 | 6分钟   | 34/34 (100%)  |

※SnezhnayaRoute只会和Cleanup额外A一起执行，请尽量使用**定时启动**来Stable激活时间以跑Cleanup额外Route。
`富B富点%提升中`
#### 经验值计算公式

`总经验 = (富点数×1.5 + 穷点数×1.35) × 420`

Path详情：[金山文档 - Path详情](https://www.kdocs.cn/wo/sl/v13uXscL)

## 四、Path结构

- **激活**：提前加载触发CD倒计时，后续可自由安排时间拾取，避免"现用现触发"的等待问题，无需WorriedCD同步问题。
- **准备**：少数点位需要提前转变为发光点，不拾取Investigating点！部分优质富点有Common Mobs镇守，清除以后才按Path顺序拾取，此时不拾取Investigating点！
- **NormalA**：至多98个Investigating点，这部分每天交叉跑，不再需要卡时间。
- **NormalB**：至多98个Investigating点，这部分每天交叉跑，不再需要卡时间。
- **Cleanup**：附近区域超出100以外的Investigating点。
- **额外**：不受满上限影响消失，又叫超限点，额外Route会受到激活时间影响，当Auto 延时累计超过(**30+最大额外等待时间**)分钟Auto 重置激活（每日Auto 延时+1分钟）。
- **SnezhnayaCleanup额外A**：玻璃罐独立200上限，是特殊的超限点，需要联机跑6个世界才能打满，现每世界34个。

### 运行时间线

```text
上一次激活时间
        │
        ├─ NormalRoute前半段（拾取，同时运行至目标时间）
        │
        ├─ 到达目标激活时间：激活 / 准备 / 清怪（不拾取）
        │
        ├─ NormalRoute后半段（拾取）
        │
        └─ CleanupRoute + 额外Route（拾取）
```

NormalRoute本身就是等待目标激活时间的一部分操作，不会先单独空等 24 小时；到达目标时间后才执行激活、准备和清怪操作。

## 五、队伍Configuration建议

- **根据自己CPUConfiguration选择合适的移速**：电脑性能较差以至于收益远不如及格线时，降低队伍移速（使用较矮小的体型，不使用双风，Lost Prayer to the Sacred Winds，迪西雅天赋等）。
- **行走位**：优先Dehya；或Barbara等 E启动奶。
- **The BellDehya**：耐肘王/白天6-18点移速+10%（js自定义Configuration可选调时间到白天，全程100%吃满天赋）。
- **Kaedehara Kazuha**：建议携带，Path内配有E吸Artifact EXP策略（不带不影响运行），琴可作为备选项，不要同时携带琴和Kaedehara Kazuha。
- **双风BUFF**：移速+10%，体力消耗-15%。

## 六、OtherFAQ

- **为什么不捡东西了**：检查自己的分辨率是否为1080p（更高或更低都不保证能正常运行），检查是否修改过按键。
- **为什么比预期少了很多**：
  1. 可能运行了OtherRoute等误触了Investigating点。
  2. 首次运行建议比前一天运行任何OtherArtifact EXP更晚，否则可能存在部分点位未刷新。
  3. 电脑性能较差，容易跑偏/跑过头，建议降低画质等，并关闭不必要的Other程序。
- **这个js好慢，不像abe四十分钟就跑完了**：那就用abe。
- **想要捡Artifact EXP的时候也能捡Other东西**：去锄地All-in-One Runjs中获取相关物品图片放在本js的assets/targetItems中。
- **出现报错**：如果还在动就不用管他，可能是正常的
- **想要测Author怎么办** ：来q群1109232869测测莫酱（有Other问题也建议加群反馈），Alternate群1022240522

- **茶包版小广告**：茶包版bgi有独有的联机锄地逻辑，如果感兴趣也可以加上面群了解。
- **问题反馈**：不接受github渠道的问题反馈，只接受通过qq渠道反馈
- **莫酱全家桶（部分）**：
  - 日常使用
  - 锄地All-in-One Run：一站式解决Auto 化锄地，Supports只拾取Artifact EXP
  - AAAArtifact EXP批发：Auto 卡时间拿Artifact EXP，收益最大化
  - AAAArtifact EXP联机团购：联机获取更多Artifact EXP收益
  - Gathering CD Management：管理采集Route并Auto 优化
  - 锁定四星Instructor：锁定四星Instructor，Supports筛选只要初始3和只要带充能
  - 只要大瓶：尽可能将Artifact EXP分解成大瓶，起个好看的作用
  - 妙妙小工具
  - 性能测试：测测你的电脑性能
  - Food Processing Turbo Version：与Gathering CD Management中相同的Food Processing
  - 更多妙妙小工具可以加群获取
