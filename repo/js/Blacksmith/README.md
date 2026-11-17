# Auto 锻造魔矿脚本

## ⚠️ 免责声明

> **重要提示：请在使用前仔细阅读以下内容**

### 使用风险

本脚本为开源Learning项目，仅限个人Learning使用，**禁止用于商业用途或任何违反游戏条款的行为**。滥用可能导致游戏Account封禁，开发者不承担任何直接或间接责任。

### 责任限制

本脚本按"现状"提供，不承诺兼容性、安全性或Features完整性。因使用本脚本导致的Account、数据、设备等任何损失，开发者概不负责。

### 禁止条款

严禁对本脚本进行逆向工程、恶意篡改或用于外挂等非法用途。如游戏运营商提出要求，开发者保留随时停止维护的权利。

**使用本脚本即表示您已阅读、理解并同意上述所有条款。**

## 📞 联系与反馈

如有任何建议或问题，欢迎通过以下方式联系：  
📧 QQ：1765137214（本人已退游，欢迎后续来者优化/更新）

---

## ✨ Feature Overview

适用于原神 7.0
BGI 0.64.0 Version
本脚本能够Auto Go to指定Blacksmith，通过智能图像识别技术Auto 选择或按预设优先级锻造魔矿：

- 🗺️ **Auto 寻路** - 智能导航至指定Blacksmith
- 🔍 **矿石识别** - Supports多种矿石的Auto 识别与选择
- 🎯 **双模式锻造** - 提供Auto 和手动两种智能模式
- 📊 **状态通知** - 实时桌面通知与详细执行Log
- 🛡️ **Exception / Error处理** - 智能应对各种Exception / Error情况

## 📁 文件结构

```
Auto 锻造魔矿脚本/
├── main.js              # 核心业务逻辑
├── manifest.json        # 脚本元信息与基础Configuration
└── settings.json        # 用户自定义Configuration文件
```

## 🚀 FastStarting Up

### 1. 安装脚本

将本脚本添加至 BGI 脚本调度器。

### 2. Configuration参数

右键点击脚本，选择"编辑 JS Configuration"或直接修改 `settings.json` 文件：

```json
{
    "smithyName": "FontaineBlacksmith",
    "CondessenceCrystal": "Condessence Crystal",
    "CrystalChunk": "Crystal Chunk",
    "AmethystLump": "Amethyst Lump",
    "RainbowdropCrystal": "Rainbowdrop Crystal",
    "notice": true,
    "forgedOrNot": "是",
    "model": "模式一"
}
```

### 3. 矿石ConfigurationGuide / Instructions

**默认Supports矿石**：

- Crystal Chunk
- Amethyst Lump
- Condessence Crystal
- Rainbowdrop Crystal

**矿石优先级Guide / Instructions**：

- 每种矿石的优先级可在 `settings.json` 中Configuration，数值范围为 `0-4`。
- **优先级为 0**：表示不使用该矿石，脚本会Auto 排除。
- **优先级为 1-4**：数值越小，优先级越高。
- **优先级相同时**：按照矿石的默认顺序（Condessence Crystal > Crystal Chunk > Amethyst Lump > Rainbowdrop Crystal）决定使用顺序。

## ⚙️ Features详解

### 🔧 锻造模式

| 模式               | 描述                                                                                             |
| ------------------ | ------------------------------------------------------------------------------------------------ |
| **模式一（Auto ）** | Auto 识别Inventory中数量最多的矿石进行锻造，识别Defeat时Auto Switch到手动优先级模式（可能存在数量识别错误） |
| **模式二（手动）** | 按照用户Configuration的优先级顺序，依次尝试主选及备选矿石                                                 |

### 🎯 特殊Features

- **仅领取锻造**：如选择"否"，则仅检测并领取已完成的锻造奖励
- **智能兜底**：Auto 模式识别Defeat时，Auto Switch到手动优先级模式
- **通知与Log**：Supports桌面通知和详细Log，便于追踪脚本执行状态
- **Exception / Error处理**：多次识别Defeat、材料不足等情况均有详细提示和Auto 处理
- **优先级排序**：脚本会根据用户Configuration的矿石优先级进行排序，优先级为 0 的矿石会被Auto 排除。

## 📋 使用Precautions / Notes

1. **环境要求**：确保游戏分辨率、BGI Version与脚本要求一致
2. **窗口状态**：运行脚本时请保持游戏窗口处于前台且未被遮挡
3. **权限Settings**：确保已授予脚本必要的系统权限
4. **权限Settings**：部分模块由于使用了Shortcut Keys，请确保Shortcut Keys为默认值。例如NatlanBlacksmith以及仅领取锻造前检查，使用地图Shortcut Keys"M"；模式一Minerals识别部分，使用InventoryShortcut Keys"B"。因为模式一调用了OCR，数字识别部分可能出现错误
5. **矿石优先级Configuration**：请确保至少有一种矿石的优先级大于 0，否则脚本将停止运行并提示错误。


## 📋 自定义扩展：添加新矿石与Blacksmith

本脚本Supports用户自定义添加新的矿石种类和BlacksmithRoute。请严格按照以下步骤操作。

---

### 🔧 添加新矿石

#### 1. 添加锻造界面图片

- 截图【锻造界面】中矿石Top-Right角的小图标，建议尺寸 21×21 像素。
- 保存为 PNG 格式，放在 `assets/Picture/` 目录下。
- 文件名建议使用英文且不含标点和空格，例如：`NewOre.png`。

#### 2. 添加Inventory界面图片

- 截图【Inventory界面】中对应矿石的图标，建议尺寸 75×75 像素。
- 保存为 PNG 格式，放在 `assets/RecognitionObject/ItemImage/` 目录下。
- 文件名同样建议使用英文且不含标点和空格，例如：`NewOre.png`。

#### 3. 修改 main.js 文件

在 `main.js` 文件顶部，依次在以下区域添加新矿石信息
- 【用户Configuration】
- 【OreChineseMap】
- 【orePriorityConfig】
- 【nicknameOrder 】
- 【ingredientImageMap】
- 【Inventory界面物品图标】
额外的，部分区域的新增需要添加【,】符号

### 4. 添加矿石信息进setting.json文件
在`setting.json`文件末尾，根据【新增示例】添加新矿。


  ## 🔧 添加BlacksmithRoute

### 1. 录制Path
1. 使用Path录制工具录制Go toBlacksmith的Path
2. 保存为 JSON 文件，命名格式：`【地区名】Blacksmith.json`,如：`冰国Blacksmith.png`
3. 放在 `assets/assets/Pathing` 目录下

### 2. 添加Route信息进setting.json文件
在`setting.json`文件，找到【Blacksmith地区选择（默认：MondstadtBlacksmith）】，根据【新增示例】添加信息。


## ❓ FAQ

Q：脚本运行后无反应？
**A**：请按以下步骤排查：

1. 检查游戏分辨率是否符合要求
2. 确认 BGI Version是否为 0.48.2 或更高
3. 验证脚本Configuration是否正确
4. 确保游戏窗口处于前台且未被遮挡
5. 确认游戏Shortcut KeysSettings为默认值（特别是地图"M"和Inventory"B"键）

Q：OCR识别矿石数量不准确怎么办？
**A**：这是OCR技术的固有局限性，可尝试：

Switch到模式二（手动优先级模式）

---

## 📜 Changelog

### 2.4.3`(2026-08-29)`

- **优化**：NatlanBlacksmithRoute
- **新增**：
    1. Supports冰国SnezhnayaBlacksmith

### 2.4.2`(2026-04-28)`

- **新增**：
    1. README文件新增【自定义扩展】模块；
    2. 文件内增新增 Minerals/Route【新增示例】，以便于后续自定义增添Minerals。


### 2.4.1`(2026-01-11)`

- **修复**：
    1. 对话界面点击锻造图标Defeat，卡住的问题

### 2.4.0`(2025-11-29)`

- **优化**：NatlanBlacksmithRoute可能出现跑过头的问题
- **新增**：
    1. Supports月国Blacksmith，矿石Rainbowdrop Crystal的使用
    2. 重构全新的矿石使用排序方式
    3. 选择矿石排序为0时，可以排除对应矿石

### 2.3.1`(2025-08-30)`

- **修复**：
    1. 模式一识别开启通知时，发送通知报错
    2. 模式一Inventory界面不退出的问题

### 2.3.0`(2025-08-28)`

- **修复**：FontaineBlacksmith跑过头导致Defeat的问题
- **优化**：仅领取锻造时，先检测大地图Top-Left角是否有【锻造奖励】图标
- **新增**：
    1. 模式选择（默认模式一）
        - 模式一：Auto 识别Inventory中数量最多的矿石锻造，DefeatAuto Switch到手动优先级（可能存在数量识别错误）
        - 模式二：手动优先级，依次尝试主选及备选矿石
    2. SupportsNatlanBlacksmith

### 2.2.1`(2025-08-03)`

- 加快锻造速度
- 优化通知逻辑，减少通知被吞概率

### 2.1

- 使用新版Version号
- 5.7 提高了锻造上限，锻造次数由 3 改为 4

### 2.00523（2025-05-23）

- 新增仅领取锻造
- 优化点击逻辑
- 修复锻造点击次数超过 3 次的 bug

### 2.0（2025-05-22）

- 新增矿石不足时Auto 选择Alternate矿石

### 1.40521（2025-05-21）

- 新增矿石未能识别时Auto 选择Alternate矿石

### 1.4（2025-05-20）

- 新增通知Features

### 1.3（2025-05-15）

- 修复选择"Condessence Crystal"时无法识别的问题
- 仓库内新增标签

### 1.2（2025-05-12）

- 修复选择"Condessence Crystal"时无法识别的 bug

### 1.1（2025-05-01）

- 优化矿石选取方式，改用识图模式

---

**最后更新**：2026 年 04 月 28 日  
**维护者**：@呱呱z

> 💡 提示：建议定期检查更新以获取最佳体验和最新Features
