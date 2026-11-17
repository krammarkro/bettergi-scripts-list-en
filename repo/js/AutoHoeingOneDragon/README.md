# 锄地All-in-One Run

## 一、Features与运行前提

本脚本用于在 BetterGI 中执行地图追踪Route，并提供Route选择、Path分组、物品拾取、物品黑名单、药品检测、Crystalfly辅助传送、泥头车和运行Recording等Features。

- 依赖 BetterGI 的 JavaScript 脚本、地图追踪、图像识别和实时触发器接口。
- 主要识别区域按照 `1920×1080` 游戏窗口制作，Other分辨率未经过同等验证。
- 运行Route时需要使用当前 BetterGI Version能够识别的地图追踪文件和Combat策略。
- 脚本通过 BetterGI Configuration组启动，Configuration组中的队伍、Combat策略和OtherFeatures可能影响运行结果。
- 图像识别效果可能受到窗口尺寸、缩放、HDR、滤镜、插帧和Other显示Settings影响。
- 脚本不判断Character组合是否合理，也不会因为Character组合触发提示或终止运行。`validateTeamMembers` 仅用于确认用户指定的Character是否位于当前队伍中。

## 二、Fast上手

### 正常模式

最简Configuration如下：

- `operationMode`：`运行锄地Route`
- `groupIndex`：`Path组一`
- `accountName`：填写账户名称，单账户可使用默认值
- `targetEliteNum`：`400`
- `targetMonsterNum`：`2000`
- `pickup_Mode`：按需求选择模板匹配拾取、BGI 原版拾取或不拾取

需要脚本Switch Party时填写 `partyName`，否则留空。首次运行可以先选择“DebugRoute分配”查看Route分组，再选择“运行锄地Route”。

### 仅指定怪物模式

最简Configuration如下：

- `operationMode`：`启用仅指定怪物模式`
- `targetMonsters`：填写目标怪物名称，多个名称使用中文逗号分隔
- `partyName`：按需填写队伍名称
- `pickup_Mode`：按需求选择拾取方式

该模式会在Route文件名和Route描述中匹配目标怪物，只运行匹配到的Route，不使用NormalRoute组合选择逻辑。

## 三、配队建议

以下仅作建议，并非强制要求，基于开发时的 BGI 与原神Version，随着Version更新可能过时，一切以用户实际运行情况为准。

### 盾奶位

可以考虑携带盾位和治疗位，以提高Route运行的Stable性。不建议同时携带两个盾位，双盾的盾量不会叠加。

### Auto 索敌Character

可以考虑使用Auto 索敌，且无需位移或位移可控的Character：

- Furina：索敌距离 25 m。
- Escoffier：索敌距离 15 m。
- Ineffa：索敌距离 10 m，双中心索敌。
- Linnea：索敌距离 25 m。
- Mavuika：火环索敌距离 15 m。
- Sandrone：BetterGI 本体自带特化，使用 `charge` 命令即可直接锁头，但需要配合队友触发对应星烁状态。

### 拾取Character

包含Elite的分组可以考虑携带Kaedehara Kazuha或琴以提高拾取率，相关分组Guide / Instructions见[进阶使用技巧中的分组用途](#分组的用途)。

### Recommended配队

以下配队仅为主观Recommended，具体以实际运行效果为准。

<details>
<summary>Recommended配队组合与特点</summary>

- `茜芙爱万`：Citlali、Furina、Escoffier、Kaedehara Kazuha。可以Stable冻结，生存能力较高，且Nope雷、火伤害不会转化Floating Fungi，但伤害可能较低。
- `火芙盾万`：Mavuika、Furina、Citlali/Nicole/Ineffa、Kaedehara Kazuha。Mavuika数值较高且具备较强的Pathing性能，可大幅缩减Pathing时间；但缺少治疗位，可能降低Stable性。
- `万芙莉机`：Kaedehara Kazuha、Furina、Linnea、Ineffa。月反应配队，新时代体系数值较高，且有Stable的盾奶。
- `桑机爱万`：Sandrone、Ineffa、Escoffier、Kaedehara Kazuha。木偶的可用配队之一，可以Stable触发星超导；木偶本身处理次数盾怪物具有一定优势。

</details>

## 四、进阶使用技巧

### 分组的用途

分组可以让不同Route使用不同的队伍、Combat策略、拾取Settings或运行时段。Route总目标仍然只在Path组一的Route选择Configuration中Settings，分组发生在Route组合选择之后。

<details>
<summary>示例：将 400 Elite和 2000 Common Mobs拆分运行</summary>

按每只Elite 2% 概率掉落价值 2520 的四星Artifact EXP、8% 概率掉落价值 1260 的三星Artifact EXP计算，Artifact EXP期望价值为：

`0.02 × 2520 + 0.08 × 1260 = 151.2`

因此，EliteRoute存在额外的Artifact EXP收益。如有条件，EliteRoute尽量携带Kaedehara Kazuha或琴以拾取Artifact EXP；实际效果与Route、队伍和Combat策略有关，以用户自己的运行体验为准。Common MobsRouteNope上述Artifact EXP额外收益，无需刻意拾取。

具体操作：

1. 在Path组一Configuration组中填写 `targetEliteNum=400`、`targetMonsterNum=2000`，并Settings `accountName`、优先关键词、排除关键词、排序和Auto 优化选项。
2. 将 `tagsForGroup2` 填写为 `Common Mobs`。脚本会把Auto 带有 `Common Mobs` 标签的纯Common MobsRoute分配到Path组二。
3. 未命中Path组二至Path组十标签的Route进入Path组一。由于脚本不会Auto 添加通用“Elite”标签，Path组一可能包含混合Route，应通过Debug输出确认。
4. 建立两个 BetterGI Configuration组，分别将 `groupIndex` Settings为“Path组一”和“Path组二”，并使用相同的 `accountName`。两个Configuration组可以分别Settings队伍、Combat策略、拾取方式和时间限制。
5. 选择“DebugRoute分配”确认 `group1` 和 `group2` 的Route及统计，再按需要运行两个Path组。多个Path组的执行顺序由 BetterGI Configuration组或调度Settings决定。

不要将总目标分别填写成Path组一的 `400-0` 和Path组二的 `0-2000`。这两个字段表示Route组合的整体目标，不是每个Path组的独立目标。

</details>

<details>
<summary>添加自定义Route</summary>

Supports标准 BetterGI 地图追踪 JSON 格式。建议先使用 BetterGI 地图追踪编辑器录制或导出Route，再将文件放入 `pathing/0-保留/` 或其子目录。Route文件的最小结构如下，`positions` 中的位置点应由地图追踪编辑器生成：

```json
{
  "info": {
    "name": "自定义Route",
    "type": "collect",
    "version": "1.0",
    "description": "Route信息：该Route预计用时60秒，预计收入0Mora，包含以下怪物：4只EliteLocal Legend倍率三。",
    "map_name": "Teyvat",
    "bgi_version": "0.45.0",
    "tags": []
  },
  "positions": [
    {
      "id": 1,
      "x": 0,
      "y": 0,
      "action": "",
      "action_params": "",
      "move_mode": "walk",
      "type": "teleport"
    },
    {
      "id": 2,
      "x": 10,
      "y": 10,
      "action": "",
      "action_params": "",
      "move_mode": "walk",
      "type": "path"
    }
  ]
}
```

脚本对Route文件的使用规则：

- 根对象需要包含 `info` 和 `positions`，位置点、移动模式、动作和动作参数应符合 BetterGI 地图追踪格式。Route能否正常执行仍由 BetterGI Version和Route内容决定。
- `info.description` 中使用 `预计用时数字秒` 提供预计时长，例如 `预计用时60秒`。
- 怪物信息使用 `包含以下怪物：数量只怪物名称、数量只怪物名称。`，例如 `包含以下怪物：4只EliteLocal Legend倍率三。`。怪物名称必须与 `assets/monsterInfo.json` 中的名称一致，否则不会计入Route的怪物数量和收益。
- `info.tags` 使用字符串数组填写标签，例如 `["水免", "High Risk"]`。标签用于优先、排除和Path组分配；自定义标签也可以通过Path或描述中的文字参与匹配。
- `info.map_name`、`info.map_match_method` 等地图字段会随Route传递给 BetterGI，建议保留编辑器导出的值。

添加后可以先使用“DebugRoute分配”确认Route是否被读取、统计和分组。

</details>

<details>
<summary>添加自定义模板图片</summary>

将 `.png` 文件放入 `assets/targetItems/Other/保留/` 或其子目录。模板文件名会作为物品名称参与识别和拾取历史Recording；文件名中的括号数值可用于Settings模板匹配阈值。使用模板匹配拾取模式时，脚本会在启动阶段加载这些模板。

模板图片可以从以下来源获取：

1. 自行截图：从游戏中的拾取列表截取物品名称区域，截图时应Note位置、大小和显示比例，尽量与运行时画面保持一致，并保存为 `.png`。
2. 采集 cd 管理：从该脚本的 `assets/targetItems/` 目录中获取需要的模板图片，再复制到本脚本的自定义模板目录。
3. 获取最新模板：Go to[交流与相关项目](#八交流与相关项目)中的 QQ 群 `1109232869` 获取。

</details>

<details>
<summary>使用Treasure HoarderFriendship任务补足Common Mobs</summary>

Treasure HoarderFriendship任务单次可以击杀 7 只Common Mobs，相比常规Common MobsRoute通常具有更高的单位任务效率。该任务最多可运行 50 次，共计 350 只Common Mobs。

如果需要提高整体运行效率，可以在调度末尾添加一个CombatFriendship任务，并勾选“无经验和Mora时提前结束”。同时将本脚本的目标Settings为Elite 400、Common Mobs 1700，即 `400-1700`，把剩余的Common Mobs目标交给Friendship任务完成。

</details>

## 五、Configuration项Guide / Instructions

Configuration项按Features分组列出，字段名称与 `settings.json` 一致。每项默认折叠，点击标题可查看详细Guide / Instructions。

### 执行Settings

<details>
<summary><code>operationMode</code>：执行模式</summary>

可选值：

- `运行锄地Route`：按Route选择和Path组Configuration执行Route。
- `DebugRoute分配`：只进行Route选择和分组，并输出Debug结果。
- `强制刷新所有运行Recording`：重新初始化当前账户的RouteRecording，不执行Route。
- `启用仅指定怪物模式`：只运行名称或描述中包含目标怪物的Route。

</details>

<details>
<summary><code>groupIndex</code>：执行的Path组</summary>

选择当前运行的Path组，范围为“Path组一”至“Path组十”。脚本每次启动只处理当前选择的Path组。使用Path组二至十时，Route选择Configuration从同账户的Path组一Configuration文件读取。

</details>

<details>
<summary><code>partyName</code>：Path组使用的队伍</summary>

填写 BetterGI 中的队伍名称。脚本会在适用的执行模式下尝试Switch到该队伍。留空时不执行指定队伍Switch。

</details>

<details>
<summary><code>validateTeamMembers</code>：队伍成员确认</summary>

填写需要确认的Character名称，多个Character使用中文逗号分隔。Switch Party后，脚本会确认这些Character是否存在；确认Defeat时会重新尝试Switch，最多重试 3 次。留空时不执行Character成员确认。该Configuration不评价队伍组合是否合理。

</details>

<details>
<summary><code>sortMode</code>：组内Route排序</summary>

可选值：

- `原文件顺序`：按Route文件名顺序运行。
- `效率降序`：按脚本计算的Route效率排序。
- `高收益优先`：将带有高收益标记的Route排在前面。

默认值：`高收益优先`。

</details>

### 拾取Settings

<details>
<summary><code>pickup_Mode</code>：拾取模式</summary>

可选值：

- `模板匹配拾取，拾取Artifact EXP和怪物材料`：加载对应目录下的物品模板进行识别。
- `模板匹配拾取，只拾取Artifact EXP`：只加载Artifact EXP模板。
- `bgi原版拾取`：由 BetterGI 的 `AutoPick` 实时触发器处理。
- `不拾取任何物品`：不启动脚本模板拾取。

默认值：`模板匹配拾取，拾取Artifact EXP和怪物材料`。

</details>

<details>
<summary><code>onlyRelatedItems</code>：只识别Route相关材料</summary>

模板匹配拾取时，根据当前Route包含的怪物筛选怪物材料模板。只拾取Artifact EXP模式Nope可筛选的怪物材料；BGI 原版拾取和不拾取模式下该选项不生效。

默认值：关闭。

</details>

<details>
<summary><code>disableSecondCheck</code>：关闭物品二次确认</summary>

关闭模板识别到物品后的二次确认。该Settings可能改变误识别和漏识别的情况，具体效果取决于模板和当前画面。

默认值：关闭。

</details>

### Route选择与分组Settings

<details>
<summary><code>accountName</code>：账户名称</summary>

用于区分 `settings/`、`records/` 和 `blacklists/` 中的账户数据。多账户运行时使用不同名称。Path组一Configuration会将Route选择相关参数保存到该账户的Configuration文件中，OtherPath组读取同一账户的该文件。

默认值：`默认账户`。

</details>

<details>
<summary><code>tagsForGroup2</code> 至 <code>tagsForGroup10</code>：Path组标签</summary>

这组Configuration项分别对应Path组二至Path组十：`tagsForGroup2`、`tagsForGroup3`、`tagsForGroup4`、`tagsForGroup5`、`tagsForGroup6`、`tagsForGroup7`、`tagsForGroup8`、`tagsForGroup9`、`tagsForGroup10` 依次对应Path组二至Path组十。每个Configuration项填写该Path组要匹配的标签，多个标签使用中文逗号分隔。

脚本按Path组编号从小到大的顺序匹配标签，一条Route命中多个Path组时分配到先匹配到的Path组。Nope命中Path组二至Path组十标签的Route进入Path组一；Path组一Nope单独的标签Configuration项，是默认兜底组。

</details>

<details>
<summary><code>targetEliteNum</code>：Elite怪总目标</summary>

Route组合使用的Elite怪总目标。脚本内部会额外预留一定数量，用于降低漏怪对目标的影响。该目标是所有选中Route的整体目标，不是每个Path组单独的目标。

默认值：`400`。

</details>

<details>
<summary><code>targetMonsterNum</code>：Common Mobs总目标</summary>

Route组合使用的Common Mobs总目标。脚本内部会额外预留一定数量，用于降低漏怪对目标的影响。该目标是所有选中Route的整体目标，不是每个Path组单独的目标。

默认值：`2000`。

</details>

<details>
<summary><code>priorityTags</code>：优先关键词</summary>

包含关键词的Route会被优先保留。匹配范围包括Route文件Path、Route描述中的怪物名称和Route标签。多个关键词使用中文逗号分隔。

</details>

<details>
<summary><code>excludeTags</code>：排除关键词</summary>

包含关键词的Route不参与Route选择。匹配范围包括Route文件Path、Route描述中的怪物名称和Route标签。多个关键词使用中文逗号分隔。

默认值：`Floating Fungi，Local Legend，狭窄地形`。

</details>

<details>
<summary><code>disableSelfOptimization</code>：关闭Auto 优化</summary>

关闭根据历史运行Recording调整Route预计用时的Features。关闭后主要使用Route文件中的预计用时。

默认值：关闭。

</details>

<details>
<summary><code>efficiencyIndex</code>：Mora与耗时权衡因数</summary>

填写 0 或更大的数字。数值越大，Route选择计算中对收益的权重越高，具体选路结果还取决于Route数据和目标数量。

默认值：`0.25`。

</details>

<details>
<summary><code>curiosityFactor</code>：Curious系数</summary>

填写 0 到 1 之间的数值。缺少运行Recording的Route会按该系数调整预计用时，以增加对未知Route的尝试。调整后显示的预计用时可能与实际用时不同。

默认值：`0`。

</details>

<details>
<summary><code>ignoreRate</code>：忽略比例</summary>

填写大于等于 0 的数值后启用。Normal怪物数量与Elite怪物数量的比例超过该值，且Route不含受Protection标签时，脚本会将该Route中的Elite数量按 0 处理，使其按Common MobsRoute参与选择。默认值 `-1` 表示关闭。

默认值：`-1`。

</details>

### 运行辅助Settings

<details>
<summary><code>activeDumperMode</code>：泥头车模式</summary>

填写需要提前释放元素战技的Character编号，多个编号使用中文逗号分隔。Route文件中包含 `keypress(T)` 时，该Route不启用泥头车逻辑。Character技能效果和Route结果取决于队伍及Combat环境。

</details>

<details>
<summary><code>eatBuff</code>：Route间使用Food / Dishes</summary>

填写Food / Dishes名称，多个名称使用中文逗号分隔。脚本会在Route之间尝试使用Food / Dishes，使用间隔为 300 秒。

</details>

<details>
<summary><code>detectRevival</code>：复活Food / Dishes检测次数</summary>

填写大于 0 的整数后启用复活Food / Dishes检测。使用次数按分钟统计，检测到目标后还需要经过多次确认。

默认值：`0`。

</details>

<details>
<summary><code>detectHealthBar</code>：回血Food / Dishes检测次数</summary>

填写大于 0 的整数后启用血条检测和回血Food / Dishes使用。使用次数按分钟统计，检测到目标后还需要经过多次确认。

默认值：`0`。

</details>

<details>
<summary><code>timeRule</code>：不运行时段</summary>

Supports `8`、`8-11`、`23:11-23:55` 等格式，多个规则使用中文逗号分隔。单独填写 `8` 时表示从 8:00 到 9:00 前；含分钟时按实际时分计算。留空表示不Settings时间限制。

</details>

<details>
<summary><code>findFInterval</code>：拾取图标识别间隔</summary>

控制两次检测拾取交互图标之间的等待时间，单位为毫秒。脚本会将该值限制在可用范围内。

默认值：`100`。

</details>

<details>
<summary><code>pickupDelay</code>：拾取后延时</summary>

控制识别并按键拾取后等待下一次识别的时间，单位为毫秒。

默认值：`50`。

</details>

<details>
<summary><code>rollingDelay</code>：滚动后延时</summary>

控制拾取列表滚动后的等待时间，单位为毫秒。

默认值：`32`。

</details>

<details>
<summary><code>timeMove</code>：滚动周期</summary>

控制拾取列表上下滚动的周期，单位为毫秒。

默认值：`1000`。

</details>

<details>
<summary><code>logMonsterCount</code>：输出怪物数量Log</summary>

Route运行结束时输出脚本传入的Elite和Common Mobs数量，便于在Log分析中核对Route数据。

默认值：关闭。

</details>

<details>
<summary><code>disableAsync</code>：禁用异步队伍Switch</summary>

调整队伍Switch相关操作的执行方式。该Settings只影响适用执行模式下的队伍Switch流程。

默认值：关闭。

</details>

<details>
<summary><code>enableCoordCheck</code>：启用坐标校验</summary>

Route结束时执行坐标校验。该Settings主要用于宿主Nope返回Route结果的情况，也会增加Route结束阶段的处理时间。

默认值：关闭。

</details>

<details>
<summary><code>useCrystalflyCatcher</code>：Crystalfly辅助传送</summary>

填写Crystalfly诱捕装置坐标，格式为 `X，Y`，使用中文逗号分隔。Happy当前位置、RouteStart和装置距离条件时，脚本会尝试打开地图并点击装置，然后传送到RouteStart。

</details>

<details>
<summary><code>targetMonsters</code>：仅指定怪物模式目标</summary>

仅在 `operationMode=启用仅指定怪物模式` 时使用。填写怪物名称，多个名称使用中文逗号分隔。脚本会在Route文件名和Route描述中进行包含匹配。

默认值：空。

</details>

## 六、脚本运行逻辑Guide / Instructions

<details>
<summary>启动和Configuration读取</summary>

脚本启动后读取当前Configuration。Path组一会将Route选择相关Configuration保存到 `settings/{accountName}.json`；OtherPath组读取该账户已经保存的Route选择Configuration。之后脚本加载拾取模板、账户黑名单和运行Recording，并根据执行模式进入对应流程。

</details>

<details>
<summary>Route选择和运行</summary>

正常模式会读取Route文件，解析预计用时、怪物数量、收益和标签，然后应用优先关键词、排除关键词、Auto 优化和Route组合算法。选中的Route按Path组标签分配，脚本每次只运行当前 `groupIndex` 对应的组。

仅指定怪物模式会直接在Route文件名和描述中匹配 `targetMonsters`，匹配到的Route进入Path组一。

</details>

<details>
<summary>Route结果处理</summary>

宿主返回包含布尔类型 `success` 的结果时，脚本直接使用该结果。宿主Nope可用返回值且启用 `enableCoordCheck` 时，脚本读取RouteStart和End并执行坐标校验。

宿主Nope返回值且关闭坐标校验时，脚本Nope可靠手段确认Route是否成功，这是宿主能力限制。Route返回Defeat、坐标校验Exception / Error、未回到主界面或检测到重连界面时，不写入本次运行时长和Route CD。

</details>

<details>
<summary>运行Recording和数据文件</summary>

- `records/`：保存账户对应的Route CD、有效运行时长和模板匹配拾取历史。
- `blacklists/`：保存物品黑名单。
- `settings/`：保存Path组一的Route选择Configuration。
- `Debug结果/`：保存Route分配Debug输出。
- `pathing/0-保留/`：保存用户自定义Route。
- `assets/targetItems/Other/保留/`：保存用户自定义拾取模板。

运行Recording默认保留最近 7 次有效运行时长，模板拾取历史默认保留最近 20 个去重后的物品名称。DefeatRoute不会加入有效运行时长Recording。

</details>

## 七、故障排查

### RouteNope被选中

检查Route是否被 `excludeTags` 排除、是否命中Route组合目标、是否属于当前Path组，以及Route描述是否包含可解析的预计用时和怪物数量。

### DebugRoute输出包含旧文件

由于 BetterGI 暂未向 JS 脚本提供删除文件的接口，执行“DebugRoute分配”时，`Debug结果/group1` 至 `Debug结果/group10` 中原有的Route文件不会被Auto 清除。因此，输出文件夹中可能同时存在本次结果和历史结果。

判断Route分配时应以 `Debug结果/Route分配结果.txt` 中的Route清单和统计为准。建议每次重新Debug前，先手动清空对应的 `group1` 至 `group10` 文件夹，再运行Debug模式。

### 拾取Nope生效

检查拾取模式、模板目录、物品黑名单和游戏窗口尺寸。模板匹配模式需要有效模板；BGI 原版拾取依赖宿主的 `AutoPick` 实时触发器。

### RouteRecordingNope更新

检查宿主是否返回 `success`，或是否开启坐标校验。RouteDefeat、未回到主界面、坐标Exception / Error和重连状态都会跳过Recording更新。

### Crystalfly辅助传送Nope触发

检查坐标格式、地图坐标、Route文件中的Start坐标以及Crystalfly装置是否位于识别范围内。该Features只在当前位置与装置位置Happy距离条件时触发。

### 队伍SwitchDefeat

检查 `partyName` 是否对应 BetterGI 中的队伍名称。填写 `validateTeamMembers` 后，脚本还会确认指定Character是否存在；未填写时不会进行Character成员确认。

## 八、交流与相关项目

- QQ 群：1109232869。
- 茶包版 BetterGI 包含独立的联机锄地逻辑，可在上述群聊中了解相关信息。
- 相关工具包括：锄地All-in-One Run、AAA Artifact EXP批发、AAA Artifact EXP联机团购、采集 CD 管理、锁定四星Instructor、只要大瓶、妙妙小工具、性能测试和Food Processing Turbo Version。
- 使用过程中可以通过上述群聊反馈问题和交流Configuration经验。
