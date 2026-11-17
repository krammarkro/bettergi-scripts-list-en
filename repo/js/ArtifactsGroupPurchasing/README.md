# AAA Artifact EXP联机团购
> **Note：此Features需配合莫酱联机工具才能实现联机**
## 一、Features及部分原理Guide / Instructions
1. **联机团购的核心原理**：多人轮流当房主，其余成员进入房主的世界占位加载Investigating点。因为每个玩家的世界有**各自独立**的Investigating点（每天各自刷新上限），所以 N 个人轮流当房主、去各自的世界收获这些被队友加载的额外Investigating点。这是「团购」相对单人Artifact EXP批发的收益来源。
2. **Character分工** ：（通过编号判定，0=单人 / 1=房主 / >1=队员）：
   - **房主（1 号）**：在自己的世界里跑完整Route（前执行 → 后执行），是收益的主要采集者。
   - **队员（2/3/4 号）**：进入房主世界后，仅用「占位」Route占住对应序号的格子（Skip完整Route、避免抢点/卡位），等房主跑完该世界后离开。
3. **两种相互独立的附加Route开关** ：（均默认关闭，互不牵连）：
   - （前执行 / 额外Route）：联机Cleanup后单人运行时勾选，运行「额外/前执行」分支。
   - （Snezhnaya罐罐）：附加独立Route（「额外/Snezhnaya」），与前者相互独立，可单独开关。
4. **Supports断点续跑与收益上报**：脚本会向 mojang 团购服务端上报每局经验/Mora，服务端负责排行榜、收益上限与炸车Auto 冻结（详见 [第四·服务端Guide / Instructions](#四运行原理)）。
5. **SupportsAuto 重新**：配合 mojang联机工具，可在联机结束后Auto 重新上线。

## 二、Usage及Configuration

1. 从莫酱联机工具处将脚本更新至 BetterGI 调度器。
2. 右键点击脚本以修改 JS 自定义Configuration。逐项含义如下：

### 联机运行Configuration
- **运行模式**：。
  - `使用JSONConfiguration文件`：从 `匹配信息.json` 读取联机信息Starting Up联机。
- **运行时使用队伍（partyName）**：进入联机模式前Switch到的队伍名。
- **运行时使用Character的序号**：进入联机前尝试Switch到的Character序号。

### CleanupRouteConfiguration
- **1p CleanupRoute**：1 号（房主）自家世界跑的CleanupRoute，可选 `Fontaine高塔 / 茶叶 / Seiraimaru / Windrest Flower`，默认 `Fontaine高塔`。非必要不建议更改。

### 额外RouteConfiguration
- **运行额外Route / 联机Cleanup**：联机Cleanup后单人运行勾选；Normal模式勾选后运行「额外/前执行」分支；Auto 进入模式在联机完成后立即执行额外Route。
- **运行Snezhnaya罐罐Route**：附加独立Route（「额外/Snezhnaya」），勾选后才会执行，与「额外Route」相互独立，请在额外Artifact EXPConfiguration组中勾选。

### OtherConfiguration
- **禁用强迫症模式**：勾选后即使人不齐也执行Route。
- **Debug**：勾选后跳过Route执行逻辑，仅供Debug。
- **Auto 重新上线**：联机结束后Auto 用 `匹配信息.json` 在 mojang 重新上线；填所需最小上线次数，炸车后重新上线不消耗次数，正常当房主跑完一次后Auto 改为不当房主；填 0 仅运行一次即停，想确保当上房主请填 >0（如 1）。
- **完成 2/3p Route后提前踢出**：对应占位成员Route跑完即踢出。
- **联机等待All-in-One Run / 联机后All-in-One Run**：炸车或正常结束后重新上线时 / 正常结束且不再上线时启动的All-in-One Run（需配合 mojang联机工具）。
- **放人模板匹配使用全部图片**：关闭时为每个白名单队员选择文件名最相似的图片。
- **是否通知信息**：打印Log，建议开启。
- **拾取匹配阈值**：误捡调高、漏捡调低，默认 `0.9`。
- **识别间隔毫秒**：两次检测 F 图标之间的等待，默认 `100`。

## 三、FastStarting Up

### 运行前提
- 游戏画面Recommended `1920×1080` 分辨率（识别区域/点击坐标按此Configuration）。
- 游戏按键保持默认，尤其是Investigating/拾取 `F` 键。
- 联机工具与BGi都是管理员权限运行

### 联机Account限制
- **账户名称** ：
   - 队伍名不得包含 `\\ / : * ? " < > |`，不能以空格开头或结尾，不能使用 Windows 保留设备名，长度 ≤ 255。
- **联机规则** ：
   - 联机基于公平互利原则
   - 不允许手动中途跳车
   - Other原因导致的炸车也会对过错方进行惩罚
- **多Account管理** ：
   - 有多个Account参与联机时，每个Account使用独立的 BGI 和莫酱用户端文件夹


## 四、运行原理

### Route目录结构
脚本Route位于 `assets/ArtifactsPath/`，按「地点」分组，每组含若干阶段子目录：

| 目录 | 含义 | 谁跑 |
|---|---|---|
| `地点/前执行` | 在 2/3/4 号进入**前**，由房主在自家世界执行 | 房主 |
| `地点/后执行` | 踢出 2/3/4 号后，房主补跑的Cleanup | 房主 |
| `地点/占位` | 队员进入房主世界后占住对应序号的Route | 队员（2/3/4 号）|
| `额外/前执行` | 联机Cleanup后单人附加Route| 房主单人 |
| `额外/Snezhnaya` | Snezhnaya罐罐附加独立Route| 房主单人 |

常见地点分组：度假村、智障厅、Fontaine高塔、Seiraimaru、茶叶、Tatarasuna等（依Version更新增减）。

### 运行时间线（手动上线示意）
```text
填写游戏名/UID点击上线进入妙妙屋联机房间（人齐发车）
        │
        ├─ 房主在自家世界：前执行Route，做一些前置准备。
        │
        ├─ 等待队友进入自己世界。
        │
        ├─ 队友执行占位逻辑，各自Go to占位点，房主执行占位检查，不通过判定为炸车。
        │
        ├─ 房主Starting Up执行Artifact EXP拾取Route。
        │
        ├─ 房主完成 2/3/4 号Route后提前踢出各Route占位成员。
        │
        ├─ 房主后执行CleanupRoute。
        │
        └─ 额外Configuration组：房主单人再跑额外/Snezhnaya附加Route。
```

### mojang 团购RecordingGuide / Instructions
JS 脚本只负责采集与上报；**收益Recording、收益上限、炸车冻结、排行榜**由独立的 mojang 服务端处理：
- **收益上限**：单次经验或Mora > 15 万会被处理（反作弊），单日经验+Mora合计 > 26 万在排行榜侧归零。
- **炸车Auto 冻结**：当天作为过错方参与炸车，Normal用户达 2 次、信任用户达 100 次即Auto 冻结并下线。
- **排行榜**：为收益Showing Off用，不含限制逻辑。
- **积分制度** ：
   - 发车时房主消耗 3 分，队员获得 1 分（每日首次占位额外获得 1 分）
   - 炸车时，过错方扣除 6 分，补偿其余参与者一人 2 分
   - 多次炸车还会触发冻结机制
   - 互相占位时，积分最高的将能够优先成为房主
   - 不排除积分以后还有OtherFeatures
- **联机顺序** ：
   - 积分高者优先当房主
   - 群友联机互惠互利，也有大佬的小号池专用辅助占位。

## 五、队伍Configuration建议
- **房主（1 号）行走位**：优先Dehya（耐肘王、提供移速）或Kaedehara Kazuha（吸Artifact EXP）。
- **移速**：电脑性能一般时降低队伍移速（矮小体型、不用双风等），收益更稳。
- **占位成员**：优先风属性Character。

## 六、FAQ
- **联机Artifact EXP将使用莫酱开发的专用联机工具联机，需要先跑联机Route测试JS，测试合格后才能参与。**
- **仅供有过运行Artifact EXP批发经验、会使用 BGI 的玩家参与；基础 BGI 使用问题请Go to大群。**
- **想要工具测Author怎么办** ：q群1109232869测测莫酱（有Other问题也建议加群反馈），Alternate群1022240522
- **收益情况** ：每天可获约18万Artifact EXP与4万Mora，Snezhnaya新增2万Artifact EXP与5千Mora，时间消耗110分钟。
- **为什么不捡东西了**：检查分辨率是否为 1080p（更高/更低不保证正常运行），检查是否修改过 `F` 等按键。
- **为什么比预期少**：可能运行了OtherRoute误触Investigating点；首次/换人后建议比前一天更晚运行以免点位未刷新；电脑性能差易跑偏，建议使用兼容模式或关多余程序。
- **Auto 进入/重新上线没反应**：确认 mojang 在后台正常运行、UID/名称图片与游戏内一致。
- **出现报错**：若还在正常运行可先不管，可能是正常抖动。
- **问题反馈**：不接受 GitHub 渠道反馈，只接受 QQ 渠道反馈。
- **莫酱全家桶（部分）**：
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