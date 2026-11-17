# 全Auto 周一（AutoMonday）

一站式执行《原神》中的多项每周、每月任务，包括参量质变仪、EscoffierFood / Dishes、Battle Pass Weekly、四方八方之网、投资券和星尘兑换。

## Features

- 参量质变仪：选择投入材料，并使用Electro Crystal或法器Character充能
- EscoffierFood / Dishes机关：独立启用、独立选择充能方式
- Battle Pass Weekly：Cooking、锻造、Boss击败和DomainChallenge
- 纪行满级检测：达到 50 级后，可按任务分别跳过Battle Pass Weekly
- 每周购买四方八方之网
- 每周提交投资券
- 每月使用星尘兑换Intertwined Fate、蓝球
- 多账户冷却Recording；任务Defeat后继续执行后续任务

## Usage

1. 将本脚本添加到调度器。
2. 右键脚本，打开 JS 自定义Configuration。
3. 按需启用任务并填写相关Configuration。
4. 阅读本Guide / Instructions及Precautions / Notes后，勾选“我已认真阅读 README”。
5. 从游戏主界面启动脚本。

建议首次运行时只启用一个任务，确认Path、队伍和Combat策略均可正常使用后，再逐步启用Other任务。

## ConfigurationGuide / Instructions

| Configuration | 何时需要 | Guide / Instructions |
| --- | --- | --- |
| 账户名称 | 多账户使用时 | 用于区分各账户的冷却Recording；单账户可留空 |
| 质变仪任务 | 按需 | 可选择材料与充能方式 |
| 质变仪队伍 | 选择“法器Character充能”时 | 填写包含充能Character的队伍名称 |
| Escoffier任务 | 按需 | 与质变仪任务互相独立，分别Recording冷却时间 |
| Escoffier队伍 | 启用Escoffier任务时 | 必须是包含Escoffier的队伍 |
| 纪行满级跳过项 | 按需 | 可分别跳过Cooking、锻造、Boss和Domain任务 |
| Cooking任务 | 按需 | 填写菜品名称和制作数量 |
| 锻造任务 | 按需 | 可选择Crystal Chunk、Amethyst Lump或Condessence Crystal |
| Combat队伍 | 启用Boss或Domain任务时 | 需同时Configuration对应的Auto Combat策略 |
| 四方八方之网、投资券 | 按需 | 首次使用前请确保对应区域已解锁 |
| Intertwined Fate、蓝球兑换 | 按需 | 每月各自独立执行 |

## 重要Precautions / Notes

1. Cooking任务所选菜品必须已解锁“Auto Cooking”，并准备足够材料。
2. 锻造任务固定执行 20 次，请提前准备足够矿石。
3. Electro Crystal充能速度较快，但可能受附近怪物或水晶采集状态影响；法器Character充能较Stable但速度较慢，目前仅SupportsBarbara。
4. Escoffier和参量质变仪是两个独立任务，队伍、充能方式与冷却Recording互不影响。参量质变仪完成后按 **6 天 22 小时**Recording下次执行时间。
5. 质变材料默认使用Mint。若需使用Configuration列表之外的材料，可替换 `assets` 中对应的识别图片；替换前后材料须位于Inventory同一分类，文件名保持不变。
6. 只要启用任一“纪行满级时跳过”选项，脚本就会在任务Starting Up前检查一次纪行等级。检测Defeat时会继续执行任务，避免误跳过。
7. Boss任务使用Pyro Regisvine、Cryo Regisvine场景；Domain任务使用太山府中的牛头人与讨债人场景。请提前Configuration可用的Combat策略。
8. 四方八方之网和投资券任务需要提前解锁相关地图或任务。投资券相关Achievements完成后，请关闭对应选项。
9. 脚本会将任务冷却Recording保存在本地 `record` 目录中。更新脚本时请保留该目录。
10. 部分Weekly一周只能实际测试一次，若遇到问题，请附上Log和复现步骤反馈。

## 免责声明

- 本项目仅供Learning与交流，请勿用于商业用途或违反游戏条款的行为。
- 脚本按“现状”提供，不承诺兼容性、安全性或Features完整性。使用者需自行承担Account、数据和设备风险。
- Configuration及运行Recording仅保存在本地；请勿在公共设备或不可信环境中使用。
- 严禁恶意篡改或将本项目用于非法用途。若游戏运营商提出要求，开发者保留停止维护的权利。

使用本脚本即表示您已阅读并同意上述Guide / Instructions。

---

## Changelog
### 1.4.5（2026.08.13）
1. 修复EscoffierElectro CrystalPath中寻路成功时会多一次寻路，导致Escoffier任务Defeat的bug
### 1.4.4（2026.07.28）
1. 优化Settings界面
2. 补充EscoffierElectro CrystalPath
3. 勾选满级纪行跳过后，任务cd为每周一四点刷新
### 1.4.3（2026.07.25）
1. 分离质变仪与Escoffier任务，现为两个独立任务
2. 移除Crystalfly诱捕装置任务
3. 增加纪行等级满级判断，可分别选择纪行满级时跳过Cooking、锻造、Boss和Domain任务
### 1.4.2（2026.06.15）
1. 修改任务「质变仪&Escoffier」的冷却时间为6天22小时
### 1.4.1（2026.06.01）
1. 在任务「质变仪&Escoffier」的“法器Character充能”中，增加传送完成后的等待时间，避免因Inventory打开Defeat导致的任务Defeat
### 1.4（2026.01.26）
1. 添加了每月兑换Intertwined Fate蓝球的Features
2. 修复了一些bug
### 1.3.8（2026.01.19）
1. 修改了Settings界面丑的批爆的分隔符
### 1.3.7（2026.01.14）
1. 修复了部分bug以及描述不合理的地方
### 1.3.6（2025.12.09）
1. 规范识别范围，避免直接使用genshin.width
### 1.3.5（2025.11.05）
1. 修复了Auto DomainChallengeFeatures启动Defeat原地Combat直到超时的bug
2. 修复了Debug信息无法显示的bug（实际上是忘记写了，Ehe~）
3. 修改了主函数部分，将原本的笨蛋写法改为了更直观更优雅的写法
### 1.3.4（2025.11.04）
1. 针对资源释放重构了文字识别代码
2. 优化了部分代码，添加了Debug信息
3. 修复了购买四方网偶尔会Defeat的bug
### 1.3.3（2025.10.27）
1. 修复了部分设备在某些任务运行结束后未能及时回到主页面导致后续任务无法正常执行的bug
2. 修复了偶尔会被Electro Crystal摸到的bug
3. 修改了多不合理、不安全的地方
### 1.3.2（2025.10.24）
1. 修改了账户名的获取逻辑：删除了原有的ocr获取uid，改为手动输入的方式（历史Recording会受到影响，但避免了后续出现bug的可能性）
### 1.3.1（2025.10.09）
1. 完善了法器Character充能模式的相关逻辑
2. 修复了部分描述不符的地方
3. 优化了部分不合逻辑的地方
### 1.3（2025.10.08）
1. 修复了record文件更新后丢失的问题
2. 修复了偶现的质变仪无法使用的问题
3. 添加了质变仪和Escoffier的法器Character充能Features，Electro Crystal被开采后也不用Worried了！
### 1.2.1（2025.10.07）
1. 修复了投资券Features偶现的无法使用的bug
2. 修复了质变仪Features偶现的无法使用的bug
3. 修改了运行逻辑，某处任务执行Defeat不再影响后续任务的执行
4. 优化了部分Features
### 1.2（2025.10.06）
1. 添加了Auto Battle Pass Weekly-DomainChallenge的Features
2. 添加了Auto Battle Pass Weekly-每周做菜的Features
3. 添加了Auto Battle Pass Weekly-每周锻造的Features
4. 添加了Auto Battle Pass Weekly-BossChallenge的Features
5. 添加了Auto 购买四方八方之网的Features
6. 添加了Auto 购买（提交）投资券的Features
### 1.1（2025.09.24）
1. 修复了Escoffier在做菜过程中偶现的被电死的bug（做菜做到一半人没了？别Worried，后续不会再有这种情况了！！！）
2. 完善了拦截Inventory过期物品的Features，不用每次打开Inventory之后再重复点击了！
### 1.0（2025.09.20）
1. 酱酱！“全Auto 周一（AutoMonday） V1.0”闪亮Debut！
   1. 你还在为每周的Escoffier做菜而痛苦吗？你每周的质变仪又忘记用了吗？
   2. 什么？你说脚本名字的Inspiration？因为AAA已经排不上号了，Author灵机一动，选择了反方向的AAA，至于Monday……是因为这些东西在周一刷新，所以是Monday！
2. 实现的Features 
   1. 将茶包大佬的两个脚本集成在了一起，Escoffier和质变仪可以一起收取了！同时对脚本逻辑进行了改动，采用Electro Crystal代替法器Character平A充能，速度更快了！
