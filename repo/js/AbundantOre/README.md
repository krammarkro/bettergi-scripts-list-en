# Guide / Instructions

该脚本按MiningRoute的效率从高到低Mining，Recording矿产资源的刷新时间，Auto 规划MiningRoute，可选Mining种类和挖Mining Area域。

- 脚本将在启动后持续Mining，直到以下三个条件中的**任一**条件Happy
  1. Mining的个数达到预定数值
  1. Mining持续时间达到预定数值
  1. 当前时间已过预定时间范围

        填写一个中国标准时间（CST）的时间范围或时间点。

        例如填写时间`10:30`，如果我们在`7:00`Starting UpMining，那么将在Mining约3个半小时后停止。

        例如填写时间`03:50`，如果我们在`22:00`Starting UpMining，那么将在第二天`03:50`左右停止。

        例如填写时间`23:00~03:50`，如果我们在`23:30`Starting UpMining，那么将在第二天`03:50`左右停止；如果我们在`22:30`Starting UpMining，脚本会因Nope, Not In预设时间范围内立即停止。

  如果三个条件均未填写，脚本将在挖完所有的矿后停止。Note如果第一次运行这个脚本，挖所有矿的过程可能持续十数个小时。

- 地面Mining队伍中请带**Linnea**或**Noelle**，只挖Underwater的矿则无此限制。如需进一步了解，请阅读[进阶使用](#进阶使用)中的相关内容。
- 矿产资源的刷新时间Recording在脚本目录下`local/persistent_data.json`文件中，升级或重新安装BetterGI可能导致该Recording丢失，请自行备份。
- `需要Combat的Route`提供四个选项：`正常挖`、`只跳过与Elite怪Combat的Route`、`只挖需要Combat的Route`、`全跳过`。选择`全跳过`将不运行所有需要打败怪物的MiningRoute；选择`只挖需要Combat的Route`则只运行含Combat的Route。无论哪种模式，Character仍可能在运行部分Route时被路过的怪物摸两下，请仍保证队伍有一定的生存能力。

## 进阶使用

- 如果有多个游戏帐号，可在最后一个输入框内为每个游戏帐号填写一个唯一的字符串以使他们的刷新时间分开保存，互不干扰。这个唯一的字符串并不必须是帐号的UID，只要互不相同就可以了。
- 对于因Nope完成地图探索任务而无法正常完成某些Route的玩家，如果不想跳过整个区域，可以将脚本文件名称填入`local/disabled_paths.txt`文件中以跳过这些地图追踪脚本，语法请参考`assets/disabled_paths.conf`。
- 如果一定要使用OtherCharacterMining，请在自定义Mining动作中填写相应的Character和Mining动作，例如`Dehya attack(2.0)`。也可填写`默认`或`default`来使用全局Settings中的Mining动作。使用此选项可能导致产量下降或Other问题，对此我们不做任何保证，亦不能提供技术Supports。
- 脚本会Auto 检验队伍Character，如果希望使用LinneaMining请**不要**填写自定义Mining动作。


- 脚本会Auto Recording每条Route的实际运行时长，存储在 `local/user_records.json` 文件中，按帐号和Mining模式（Linnea/Claymore）分开保存，每条Route最多保留最近 7 次Recording。该文件由脚本Auto 维护，无Manual Required编辑。升级或重装 BetterGI 可能导致该Recording丢失，可随 `persistent_data.json` 一起备份。
- 「时长数据来源」选项决定调度时用的Route时长从哪来：
  - `根据运行Recording优化`（默认）：结合 `local/user_records.json` 的实际数据和「Curious系数」做优化估算
  - `使用Route默认数据`：完全使用 `assets/statistics.json` 中的预估值
- 「Curious系数」只在 `根据运行Recording优化` 时生效，取值 0~1，数值越大越倾向尝试跑得少的Route，帮助采集数据；0 表示不做乐观修正。

## ChangeLog

### 0.35.2
- 优化了部分Route

### 0.35.1
- 优化了部分Route

### 0.35

- 新增Snezhnaya地区MineralsRoute
- 新增「只挖需要Combat的Route」选项
- 调整默认Route的时长数据
- 优化了部分Route

### 0.34

- 新增 `local/user_records.json`，Auto Recording每条Route的实际运行耗时，按帐号和Mining模式分开存储，每条Route最多保留最近 7 次
- 新增「时长数据来源」「Curious系数」选项，可结合实际运行数据优化MiningRoute的时长估算
- Mining时长数据按Character模式分开（Linnea / Claymore）
- End校验改为「接近End」判定，兼容 SIFT 地图追踪文件
- 增加排除Snezhnaya地区的选项
- 优化了部分Route

### 0.33

- 优化了部分Route以更好适配LinneaMining

### 0.32

- 优化了LinneaMining的逻辑
- 优化了部分Route以更好适配LinneaMining

### 0.31

- 优化了LinneaMining的逻辑
- 优化了Linnea的Mining动作，special thanks to [@this-Fish](https://github.com/this-Fish)

### 0.30

- 修复若干bug

### 0.29

- 稍微优化了LinneaMining的逻辑

### 0.28

- 增加LinneaMining实验性Supports，效果不甚Stable，待针对性优化。

### 0.27

- 增加Sea of Bygone Eras、Ancient Sacred Mountain地区的Route
- 重制自定义Configuration页面

### 0.25

- 修复坐标监控逻辑中未指定地图的bug，special thanks to [@this-Fish](https://github.com/this-Fish)

### 0.22

- 增加处理过期物品的弹出窗口

### 0.18

- 修复坐标监控逻辑中的bug

### 0.16

- Log实时输出进度

### 0.15

- 子任务结束时如果坐标未变化则不写入Recording

### 0.14

- 允许用户使用BetterGI默认的Mining逻辑

### 0.11

- 增加排除Nod-Krai地区的选项

### 0.10

- 在Mining结束时发送通知消息
- 修复新获取矿石无法正确识别的bug

### 0.9

- 增加Rainbowdrop CrystalRoute

### 0.8

- 适配BetterGI 0.50.0，移除DPI缩放适配的选项

### 0.7

- 允许用户自定义MiningCharacter和动作

### 0.6

- 增加跳过与Elite怪CombatRoute的选项

### 0.5

- 更新Route规划算法

### 0.4

- 重构自定义Configuration选项

### 0.3 

- Starting Up运行之前SwitchConfiguration组中Settings的队伍（如果有）
- 增加手动启用DPI缩放适配的选项

### 0.2

- 对于较快结束的任务不写入Recording
- Supports用户自行定义要跳过的Path追踪子任务
- 输出Path追踪子任务的Starting Up和结束Log，以便于Log分析

### 0.1

- 首次发布
