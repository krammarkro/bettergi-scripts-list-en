**采集CD管理**

---

### 一、**📌 脚本定位**
1. 这是一个Auto 帮你管理"采集Route冷却时间（CD）"的工具。
2. 它会按你设定的顺序，Auto 运行不同采集Route（比如Mining、采特产），并跳过还没刷新的Route。
3. 使用模板匹配拾取，功耗低，不易误触Investigating点，自带Inventory满识别并与采集联动（满Inventory材料加入黑名单并不计入Route效率计算）。

---

### 二、**🚀 Fast上手**

<details>
<summary><b>1. 准备Route文件</b></summary>

- Go to脚本仓库订阅需要的地图追踪，打开bgi文件夹，User/AutoPathing文件夹下就It's You订阅的地图追踪（Ingredients采集Recommended使用Ingredients栏目下的TeyvatIngredients All-in-One Run，内置部分Route信息）。

</details>

<details>
<summary><b>2. 极简模式</b></summary>

最简单的使用方式，将你需要的地图追踪文件全部复制到js文件夹（User/JsScript/Gathering CD Management）下的pathing中，无需考虑子文件夹层数，塞进去即可，也可尝试使用mklink等Auto 关联。

- 将js添加至Configuration组，右键js选择自定义Configuration，勾选仅刷新自定义Configuration，Path组数量填0，直接运行一次js
- 找到优先采集材料，按要求填写每天需要采集的材料和数量
- 根据材料和Path特点，Configuration合适的队伍并将队伍名称填写在自定义Configuration中的优先采集材料使用的配队名称
- 启动js，将Auto Searching相关Path，采够需要的材料或所有相关Route都被使用后js将终止
- 填写的优先采集材料是每日（以四点为界）的数量，长期运行时，js会Recording各个Route获取的数量与耗时，并据此优化，先选择效率更高的Route
- 特别的，锻造矿指代任意的Crystal Chunk，Amethyst Lump，Condessence Crystal，Rainbowdrop Crystal，填写锻造矿*160即可Happy每日锻造需求
- 循环模式提供“不循环 / 每組重试 / 全局循环”三种选项

  | 模式 | 执行逻辑 |
  | :--- | :--- |
  | 不循环 | 顺序遍历所有Path组，每个Route只跑一次，不重试 |
  | 每组重试 | 每组内反复循环，直到该组所有Route都跑满2次或都在CD中，才进入下一组 |
  | 全局循环 | 每次执行完一条Route后立即跳回第一组第一个重新扫描，优先执行未满3次的靠前Route，直到所有Route都满3次或全部CD |

  **详细示例**  
  假设有 A（A1~A3）、B（B1~B3）两组，所有RouteCD就绪：

  - **不循环**：A1, A2, A3, B1, B2, B3（结束）  
  - **每组重试**：A1, A2, A3, A1, A2, A3, B1, B2, B3, B1, B2, B3（结束）  
  - **全局循环**：A1, A1, A1, A2, A2, A2, A3, A3, A3, B1, B1, B1, B2, B2, B2, B3, B3, B3（结束）

  > 实际运行中，若某Route处于CD中，则会跳过，不影响总体逻辑。执行次数与CD状态共同决定Route是否运行。

</details>

<details>
<summary><b>3. 更进一步</b></summary>

- 一个配队不能Got it所有的采集Route怎么办，是时候启用Path组了
- Path组的作用是将Route分组运行，分出不同的优先级和配队
- 在pathing文件夹中，将Route分到不同的文件夹，第一层的每个文件夹都可供Path组选择
- 勾选仅刷新自定义Configuration，Path组数量填你需要的数量，直接运行一次js
- 再次打开自定义Configuration，为每个Path组选择对应的文件夹和使用的配队，并按要求ConfigurationOther项目
- 此外，优先采集执行时也会优先使用Path组指定的Configuration，因此你完全可以Path组Configuration后不用，只用来指定配队，临界效率填个100即可在事实上禁用该Path组的正常运行
- 正常使用Path组时，将会依次执行各个Path组，前一个Path组所有Route都未刷新或低于临界效率等不可用时，将会进入下一个Path组
- 定时终止：按要求填写定时终止，js将提前结束采集并等待到预定时间，可用于卡4点
- 不同Configuration组并不共用Configuration与Path组信息，只会根据账户名共用cd信息，因此你可以在不同的Configuration组中使用本js，Settings不同的多个Path组与终止时间，实现合理分配采集时间
- cd类型可参考js文件夹中的表格
  - “每天一次”模式（04:00–16:00采集次日04:00刷新，其余时Segment 12小时刷新）。

</details>

<details>
<summary><b>4. 采集队伍Recommended</b></summary>

根据自己想采集的物品（部分Route强制需要某些Character）进行配队。

- 当需要采集Fowl/Raw Meat等时，最好携带：Kirara等天赋不会惊动肉类动物的Character
- 当需要采集Crystalfly/Crab/Frog等，最好携带：Sayu等天赋不会惊动Other动物的Character
- （详情请搜索B站/米游社攻略，或自行查阅Character天赋与游戏图鉴）
- 当采集Sakura Bloom/Dracolite时，必须携带雷系Character，Recommended雷法：Lisa/Yae Miko等（选择一个即可）
- 采集Route有明确指定的Character也必须携带（例如Route中指定了"Nahida"）
- Recommended携带一个血牛Dehya，Path追踪行走位SettingsDehya，不容易在采集途中死亡。
- 更多详细对应采集Character请参考Route的readme，或Asking群友。

**示例：**
- 队伍名称：Dehya+Yae Miko+Nahida+琴
- 文件夹名称：特产1
- 该组可以采集：Electro Crystal/冰雾花，Sakura Bloom/Dracolite，Route中指定需要Nahida采集的，Dandelion Seed，以及Other所有无指定的采集。

⚠️ **Note**：请Note区分物品CD时间，例如上述冰雾花刷新时间与Other区域特产CD不同，尽量不要放在同一个分组，具体刷新时间请参考本脚本自带的Excel。

</details>

---

### 三、**📁 文件结构**
- main.js：主程序。
- settings.json：用于Showing OffConfiguration组的自定义Configuration面板，不影响使用。
- pathing/ 文件夹：存放地图追踪文件。
- blacklists/ 文件夹：保存各个账户名的黑名单物品信息，可以在这里手动编辑，Note需要符合json格式
- record/ 文件夹：保存各个账户名的运行Recording与cd信息

---

### 四、**⚙️ OtherGuide / Instructions**

1. **伪造Log**（不影响游戏）
   - 生成的Log可以被Log分析识别，方便查看Route运行情况。

2. **跳过Route运行后的坐标校验**
   - 勾选后，部分劣质Route，或因意外导致的卡死也将强制RecordingCD，可避免重跑。

3. **Food Processing**
   - Supports运行途中定时ProcessingIngredients如Flour等，参考自定义Configuration使用

4. **Auto 处理Exception / Error状态**
   - 运行过程中若Character被冰冻，脚本会Auto 尝试挣脱；若Character死亡，会Auto 点击复苏按钮，确保采集流程不中断。

---

### 五、**📞 联系方式**
- **QQ群**：1109232869（Alternate群1022240522）
  - 测测莫酱（有Other问题也行）
- 不接受github渠道的问题反馈，只接受加群处理

---

### 六、**📋 Schedule 执行**
<details>
<summary>点击查看详情</summary>

#### FeaturesGuide / Instructions

Gathering CD ManagementSupports执行 schedule 文件，可以将多个地图追踪或js脚本按顺序执行。

#### 文件格式

```json
{
  "schedule": [
    { "action": "start", "task": "任务名", "count": 1 },
    { "action": "wait", "task": "任务名" }
  ],
  "tasks": [
    {
      "name": "任务名",
      "type": "autopathing",
      "filePath": "Path/地图追踪.json"
    }
  ]
}
```

#### schedule 数组

定义任务执行顺序：

| 字段 | 类型 | 必填 | Guide / Instructions |
|------|------|------|------|
| `action` | string | 是 | 动作类型：`start` 或 `wait` |
| `task` | string | 是 | 任务名称，对应 tasks 中的 name |
| `count` | number | 否 | 执行次数，仅 start 有效，默认 1 |

**action 类型：**
- `start`: 启动任务，任务是否异步等待由 tasks 中 `async` 字段控制（默认 false，同步等待完成）
- `wait`: 等待异步任务完成

#### tasks 数组

定义所有可用的任务：

| 字段 | 类型 | 必填 | Guide / Instructions |
|------|------|------|------|
| `name` | string | 是 | 任务名称，唯一标识 |
| `type` | string | 是 | 任务类型 |
| `filePath` | string | 是 | 文件Path，相对于Gathering CD Management目录 |
| `settings` | object | 否 | 传递给任务的Configuration参数（仅 js 类型有效，传入脚本入口函数） |
| `async` | boolean | 否 | 是否异步执行，默认 false。设为 true 后 start 不等待完成，需搭配 schedule 中的 `wait` action |

**type 类型（大小写不敏感）：**

| 值 | Guide / Instructions | filePath 示例 |
|------|------|------|
| `autopathing` | 地图追踪 | `pathing/Mining/水晶矿.json` |
| `js` | 子脚本 | `subJs/脚本文件夹/` |
| `keymousescript` | 键鼠脚本 | `assets/滚轮下翻.json` |

#### 示例

```json
{
  "schedule": [
    { "action": "start", "task": "采集任务" },
    { "action": "start", "task": "锄地任务" }
  ],
  "tasks": [
    {
      "name": "采集任务",
      "type": "autopathing",
      "filePath": "pathing/水晶矿.json"
    },
    {
      "name": "锄地任务",
      "type": "js",
      "filePath": "subJs/AutoHoeingOneDragon/",
      "settings": {}
    }
  ]
}
```

#### Precautions / Notes

1. **Path格式**：`filePath` Path使用正斜杠 `/`
2. **识别逻辑**：读取 JSON 文件后，如果包含 `schedule` 和 `tasks` 字段，则视为 schedule 文件执行
3. **拾取Supports**：执行 schedule 期间会全程执行模板匹配交互和拾取
4. **settings 格式**：`settings` 对象格式与Configuration组文件中相同，建议在Configuration组中配好子 js 的自定义Configuration后，复制Configuration组中的部分

</details>

---

### 七、**📦 莫酱全家桶（部分）**
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

---

### 八、**📋 Changelog**

<details>
<summary>点击查看历史更新</summary>

#### 2026/08/01
1.修正循环模式"每组重试"邏輯

#### 2026/08/01
1. Auto 处理冰冻与复苏，提升长时间运行Stable性。
2. 兼容化种匣名称识别，减少漏捡。
3. 新增“每天一次”CD刷新模式，灵活适应不同采集时段。
4. 循环模式升级为下拉菜单，Supports“每组重试”和“全局循环”。
5. End坐标校验适配 SIFT Path，Supports自定义地图匹配方法。
6. 补充“刷新自定义Configuration”的Log反馈，便于确认操作。

#### 2026/2/28
1. 重构代码结构

#### 2026/2/26
1. 无f时滚轮改为仅在识别到滚轮图标时触发

#### 2026/2/18
1. 对Food Processing过程中可能出现的道具数量超过上限进行处理

#### 2026/2/17
1. 增加通知优先采集阶段和Path组Switch
2. 优化部分Log和Showing Off的自定义Configuration
3. Changelog回归

</details>
