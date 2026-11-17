# AccountSwitch工具Instructions

## FastStarting Up

### 方式一：Account图片识别（Recommended）

1. **准备Account图片**
   - **Recommended方式**：使用脚本的"截图模式"Auto 获取并保存截图（详见截图模式部分）
   - **手动方式**：在 `accounts/` 目录下放置Account截图
   - 图片命名为 `{UID}.png`，如 `284073800.png`
   - 截图应包含Account选择界面中该Account的明显标识

2. **Configuration脚本**
   - 打开BetterGIConfiguration面板
   - 填写目标AccountUID
   - 确保"跳过搜索直接输入Account密码"未勾选

3. **运行脚本**
   - 脚本会Auto 定位到Account选择界面
   - 识别并点击对应Account图片
   - Auto 进入游戏并返回主界面

### 方式二：Account密码输入

1. **Configuration脚本**
   - 打开BetterGIConfiguration面板
   - 填写目标AccountUID（用于通知显示）
   - 填写Account和密码
   - 勾选"跳过搜索直接输入Account密码"

2. **运行脚本**
   - 脚本会Auto 进入Account密码输入界面
   - Auto 点击同意按钮、输入Account密码
   - Auto 进入游戏并返回主界面

### Guide / Instructions
- **两种方式可同时使用**：方式二作为方式一的补充，当图片识别Defeat时会Auto 回退到Account密码方式
- **RecommendedConfiguration**：同时填写Account密码作为Alternate，提高Switch成功率

## 截图模式

截图模式是一个辅助Features，用于Auto 获取并保存Account图片，方便后续使用Account图片识别方式进行Switch。

**使用步骤**：
1. **Configuration脚本**
   - 打开BetterGIConfiguration面板
   - 填写目标AccountUID（优先使用，用于命名图片）
   - 勾选"截图模式"

2. **运行脚本**
   - 脚本会优先使用Configuration中的"要Switch到的AccountUID"命名图片
   - 如果未填写该项，会尝试Auto 识别当前Account的UID
   - 导航到Account选择界面
   - Auto 截图并保存Account图片
   - 返回主界面并发送成功通知

**保存位置**：
- 图片保存在 `accounts/` 目录下
- 文件名格式为 `{UID}.png`

## ConfigurationGuide / Instructions

在BetterGI的Configuration面板中进行以下Settings：

### 1. 目标AccountUID
- 输入要Switch到的AccountUID
- 用于识别Account图片文件名、通知显示和截图模式命名

### 2. Account（可选）
- 当无法通过图片识别找到Account时Alternate
- 建议填写，以防图片识别Defeat

### 3. 密码（可选）
- 当无法通过图片识别找到Account时Alternate
- 建议填写，以防图片识别Defeat

### 4. 跳过搜索直接输入Account密码
- **勾选**：不尝试查找Account图片，直接使用Account密码登录
- **不勾选**：优先尝试通过Account图片识别Switch，Defeat时回退到Account密码方式

### 5. UID校验
- **勾选**：在Switch前后检查当前AccountUID，辅助判断Switch是否成功
- **不勾选**：不进行UID校验

### 6. UID验证Defeat时尝试停止Configuration组
- **勾选**：当UID验证Defeat时Auto 终止整个Configuration组（需配合停止Shortcut Keys使用）
- **不勾选**：仅Recording错误Log，不干预后续任务
- **停止Shortcut Keys**：填写 `VK_` 格式的虚拟键码（如 `VK_F8`），需与BetterGI全局Settings一致

### 7. 截图模式
- **勾选**：进入截图模式，Auto 截图保存对应UID的Account图片
- **不勾选**：正常执行AccountSwitch流程

## FAQ

### Q: Account图片识别Defeat怎么办？
A: 确保：
1. 图片存放在 `accounts/` 目录下
2. 图片命名为正确的UID格式
3. 截图清晰，包含Account的明显标识
4. 同时填写Account密码作为Alternate方案

### Q: 提示"Account图片不存在且未ConfigurationAccount密码"怎么办？
A: 脚本在Switch前会检查Account图片是否存在。出现此提示Guide / Instructions：
1. `accounts/{UID}.png` 不存在或无法读取（可能是更新脚本后图片被清空）
2. 同时NopeConfigurationAccount密码作为Alternate

### Q: SwitchDefeat后会怎样？
A: 脚本会尝试返回主界面，并发送Defeat通知。如果Configuration了Account密码，建议手动检查Account状态。

### Q: 为什么需要填写UID？
A: UID用于：
1. 确定Account图片文件名
2. 在通知中显示Switch的Account信息
3. 截图模式下命名保存的图片文件

## Precautions / Notes

1. 首次使用前建议先手动测试一遍Switch流程
2. 确保游戏分辨率为1920x1080
3. Account图片建议截取Account选择界面中该Account的清晰截图
4. 密码输入时不会显示，属于正常现象
5. 截图模式下，默认使用Settings的目标UID，未Settings时会尝试Auto 识别
6. **更新\重新订阅脚本后 `accounts/` 目录下的Account图片可能会被清空**，请在更新后重新放入Account图片，或提前ConfigurationAccount密码作为Alternate

## 问题反馈

如果在使用过程中遇到预料之外的弹窗或Other问题，脚本可能无法处理，请按照以下方式反馈：

1. **截图保存**：截取全屏原图，确保包含完整的游戏界面和弹窗
2. **联系Author**：QQ号 718135749
3. **提供信息**：简要描述遇到的问题和操作步骤

Thank You您的Supports！

<details>
<summary>项目介绍（点击展开）</summary>

## 项目介绍

基于状态机实现的Auto AccountSwitch脚本，Supports通过Account图片识别或手动输入Account密码两种方式Switch原神Account。

### Features特性

- **双模式Switch**：SupportsAccount图片Auto 识别和Account密码手动输入两种方式
- **状态机管理**：使用有限状态机管理Switch流程，Stable可靠
- **Auto 返回**：SwitchDefeat时Auto 尝试返回原Account
- **通知提醒**：Switch成功或Defeat时发送系统通知
- **循环防护**：防止状态循环卡死
- **UID校验**：SupportsSwitch前后检查当前AccountUID，提高Switch准确性
- **智能终止** UID验证Defeat时可Auto 终止整个Configuration组
- **截图模式**：Auto 截图保存Account图片，方便后续Switch

### 目录结构

```
AccountSwitchStateMachine/
├── main.js                    # 主脚本文件
├── manifest.json              # 脚本清单
├── settings.json              # Configuration定义
├── assets/
│   ├── states.json            # 状态机Configuration
│   └── RecognitionObjects/    # 状态识别图片
│       ├── Paimon.png
│       ├── Menu.png
│       ├── PrepareToLogOut.png
│       ├── SwitchAccount.png
│       ├── Exit.png
│       ├── EnterGame.png
│       ├── LoginOther.png
│       ├── SelectAccount.png
│       ├── EnterAccountAndPassword.png
│       ├── Agree.png
│       ├── EnterAccount.png
│       ├── EnterPassword.png
│       ├── EnterGame2.png
│       ├── Login.png
│       └── Confirm.png
└── accounts/                  # Account图片存放目录
    └── {uid}.png              # 以UID命名的Account截图
```

### Working流程

```
Starting Up
│
├─► 截图模式（勾选时）
│   ├─► 使用Settings的UID或识别当前UID
│   ├─► 导航到Account选择界面
│   ├─► 截图保存Account图片
│   └─► 返回主界面
│       ├─► 成功 → 发送成功通知
│       └─► Defeat → 发送Defeat通知
│
├─► 前置检查（Account图片是否存在，Account密码是否已Configuration）
│   ├─► 图片存在 → 继续
│   └─► 图片缺失且无Account密码 → 终止并提示
│
├─► 尝试Account图片方式（未勾选跳过时）
│   ├─► 预加载Account图片
│   ├─► Switch到选择Account界面
│   ├─► 查找并点击Account图片
│   └─► Switch到主界面
│       ├─► 成功 → 发送成功通知
│       └─► Defeat → 回退到Account密码方式
│
└─► Account密码方式
    ├─► 检查Account密码
    ├─► Switch到输入Account密码界面
    ├─► 点击同意按钮
    ├─► 输入Account密码
    ├─► 点击进入游戏
    └─► Switch到主界面
        ├─► 成功 → 发送成功通知
        └─► Defeat → 尝试返回原Account → 发送Defeat通知
```

### 状态Guide / Instructions

| 状态名 | Guide / Instructions |
|--------|------|
| mainUI | 主界面（派蒙图标） |
| menuUI | 菜单界面（ESC菜单） |
| prepareToLogOut | 预备退出登录界面 |
| loginScreen | 登录界面（SwitchAccount按钮） |
| exitAccount | 退出Account界面 |
| enterGame | 进入游戏或登录OtherAccount界面 |
| selectAccount | 选择Account界面 |
| enterAccountAndPassword | 输入Account密码界面 |
| noAccount | 无Account登录界面 |

### Changelog

#### v1.2
- **新增**：Switch前检查Account图片是否存在，缺失且未ConfigurationAccount密码时提前终止并提示，避免在Switch流程中途出错

#### v1.1
- **新增**：UID验证Defeat时Auto 终止Configuration组Features，SupportsConfiguration对应键值
- **优化**：修改了Account密码界面的识别条件，修复可能会出现的误识别问题

#### v1.0
- 初始Version
- 实现状态机管理
- SupportsAccount图片和Account密码两种Switch方式
- 添加Auto 返回和通知Features

</details>