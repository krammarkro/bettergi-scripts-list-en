# BetterGI Log分析工具

一个用于分析 Better Genshin Impact Auto 化工具Log的网页工具，Supports拖放操作、多种显示模式和丰富的Shortcut KeysFeatures。

**在线地址**: https://this-fish.github.io/Read_BetterGI_Log/index.html

## 🌟 核心Features

### Log解析
- 📁 **拖放分析** - 直接拖拽Log文件到页面即可分析
- 📱 **移动端Supports** - 手机/平板设备专用上传界面
- 🔄 **多文件合并** - Auto 按时间顺序合并多个Log文件
- ⏰ **智能时间解析** - Auto 处理跨日Log和时间推算

### 数据可视化
- 📊 **详细统计** - 复活次数、重试次数、卡死点坐标等完整数据
- 🎯 **坐标追踪** - 查看死亡前最近的X/Y轴坐标
- ⚡ **实时高亮** - 鼠标悬停行高亮，清晰指示当前查看行
- 🌓 **主题Switch** - Auto /手动Switch亮色/暗色主题(00:00~06:30时Auto 暗色主题)

### 交互Features
- ⌨️ **丰富Shortcut Keys** - 20+个Shortcut Keys覆盖所有操作
- 🔍 **智能筛选** - 按任务名称关键字筛选显示
- 📈 **数据聚焦** - 隐藏零统计任务，Focused问题分析
- 📤 **导出分享** - Static模式方便截图和分享分析结果

## 🚀 FastStarting Up

### 基本使用
1. **打Time for Work!具** - 访问上述在线地址
2. **上传Log** - 拖放BetterGILog文件（文件名以`better-genshin-impact`开头）
 - BetterGILog文件所在位置如下
   - C:\你BGI所安装的目录\BetterGI\log
   - 或使用BGI打开目录
   - <img width="905" height="599"src="https://github.com/user-attachments/assets/615087a5-eead-4eb8-8028-4bfe74d9b8ff" />

3. **查看分析** - 工具Auto 解析并显示统计信息

### 移动设备使用
1. 点击"选择Log文件"按钮
2. 选择Log文件后Auto 解析
3. 使用底部Features按钮控制显示选项

## ⌨️ Shortcut Keys大全

### 显示控制
| Shortcut Keys | FeaturesGuide / Instructions | 状态指示 |
|--------|----------|----------|
| `T` | Switch时间列显示/隐藏 | Bottom-Right角提示 |
| `Y` | Switch统计列显示/隐藏 | Bottom-Right角提示 |
| `U` | Switch表格格式（新版/旧版） | Bottom-Right角提示 |
| `I` | Switch拾取物列显示/隐藏 | Bottom-Right角提示 |
| `J` | 隐藏/显示零统计任务 | Bottom-Right角提示 |
| `H` | 任务名称/Configuration组筛选（Supports排除Configuration组） | Top-Left角提示 |
| `P` | 进入/退出导出模式 | Top-Left角提示 |
| `[` | 进入/退出自由编辑网页模式 | 无 |
| `数字键4` | 只显示指定时间范围内的LogRecording | Top-Left角提示 |

### 视图操作
| Shortcut Keys | FeaturesGuide / Instructions |
|--------|----------|
| `~` | Switch亮色/暗色主题 |
| `R` | 重置所有弹窗位置 |
| `W` | 页面上滚 |
| `S` | 页面下滚 |
| `G` | 打开/关闭Configuration组导航 |
| `Alt + F` | Switch全屏模式 |
| `.` | 新标签页打Time for Work!具 |
| `Alt + L` | 显示/隐藏Features按钮区 |
| `F2` | Fast打开上传文件 |

### 计算工具
| Shortcut Keys | FeaturesGuide / Instructions |
|--------|----------|
| `6` | 计算原神下次60体力时间 |
| `7` | 计算原神下次40体力时间 |
| `8` | 计算自定义体力时间（输入:现在体力,目标体力,体力CD分钟） |
| `9` | 计算时间距离现在多久 |
| `右2` | 计算日期+3天 |
| `右3` | 计算两个时间点间隔 |
| `右5` | 计算N天后的日期 |
| `右7` | 计算原神下次120体力时间 |
| `右8` | 计算HH.MM后的时间 |
| `右9` | 计算时间+46小时后 |
| `M` | 统计指定拾取物拾取数量 | 

### 排序与筛选
| Shortcut Keys | FeaturesGuide / Instructions |
|--------|----------|
| `Alt + I` | Switch拾取物显示顺序（按数量合并/按拾取顺序） |
| `O` | 进入拾取效率模式（计算指定拾取物的秒/个效率） |
| 点击“Starting Up时间”旁边的排序按钮（↓） | Switch按读取顺序 / 按时间排序（最近的在前） |
| 点击“耗时”旁边的排序按钮（↕） | Switch耗时升序 / 降序 |
| `ESC` | 在Fast导航/筛选模式中退出 |
| `H`（在筛选模式中） | 退出筛选模式 |

> **排序按钮图标含义**：
> - **↓**：按读取顺序（默认）
> - **↑**：按时间排序（最近在前）
> - **↕**：未激活状态，点击后进入耗时排序
> - **↑（耗时列）**：耗时升序（小到大）
> - **↓（耗时列）**：耗时降序（大到小）

### 鼠标操作
| 操作 | FeaturesGuide / Instructions |
|------|----------|
| 点击Configuration组标题 | 折叠/展开该Configuration组 |
| 点击坐标单元格 | 固定/取消固定坐标弹窗 |
| 双击坐标单元格 | 重置弹窗位置到单元格中间 |
| 拖拽弹窗标题栏 | 移动弹窗位置（拖拽时Auto 固定） |
| 点击弹窗关闭按钮(×) | 关闭弹窗 |

## 📊 数据列Guide / Instructions

### 基本信息
- **任务名称** - 地图追踪任务或脚本名称
- **Starting Up时间** - 任务Starting Up执行的时间
- **结束时间** - 任务完成或中断的时间  
- **耗时** - 任务执行总时长

### 统计指标
- **复活次数** - Go toStatue of The Seven复活的次数（红色≥2次）。
  - **小数-0.9表示**：当前Character血量过低、返回Statue of The Seven回血
- **重试次数** - Route重试次数（红色≥2次）
  - **Note**：当只有重试次数而无卡死或复活时，任务名称会变为红色
- **疑似卡死** - 卡死脱离尝试次数（可查看坐标）
- **过远跳过** - 距离过远跳过的Path点（红色≥2次）
- **Combat超时** - Combat超时次数（红色≥1次）
- **传送Defeat** - 传送Defeat重试次数（红色≥3次）

### 交互Features
- **悬停查看** - 鼠标悬停统计数字显示详细信息
- **双击重置** - 双击单元格重置弹窗位置
- **点击固定** - 点击单元格固定/取消固定弹窗

## 🎯 高级Features

### H键 - 任务筛选模式
```
输入格式：包含关键字（多个用逗号分隔） /- 排除Configuration组关键字（多个用逗号分隔）
示例：Mondstadt,Liyue/-Fishing,采集   (包含「Mondstadt、Liyue」，排除Configuration组名称含「Fishing、采集」的Configuration组)
只排除：/-Fishing,采集
只包含：Mondstadt,Liyue
```
- 使用 `/-` 分隔包含和排除部分
- 多关键字逗号分隔，不区分大小写
- 筛选时Auto 隐藏所有拾取物行
- Top-Left角显示当前筛选状态

### O键 - 拾取效率模式
按下 `O` 键后，输入要计算效率的拾取物名称（多个用逗号分隔，如 `Sweet Flower,Mint`），工具将：

- 计算每个任务中指定拾取物的总数量
- 按 **“秒/个”** 的效率排序（效率高的排在前）
- 在耗时列下方显示具体数值（如 `3.5秒/1个`）
- Nope拾取物的任务排在后，不显示效率

再次按 `O` 键退出效率模式，恢复原排序。

### 数字键4 - 时间筛选模式
按下数字键4后，会显示两个时间输入框：
第一个输入框（Starting Up时间）：留空则默认为当天00:00:00
第二个输入框（结束时间）：默认为当前时间

时间格式要求：2026/01/22 18:59:00
- **FeaturesGuide / Instructions**：仅显示指定时间范围内的LogRecording
- **主要用途**：配合`M`键统计指定时间内的拾取物数量
- **Precautions / Notes**：与`H`键筛选Features冲突，不能同时使用
- **退出方式**：再次按下`数字键4`键或`H`键退出时间筛选模式

### J键 - 零统计任务隐藏
- Auto 隐藏所有Exception / Error统计值为零的任务
- 帮助聚焦有问题任务
- 与筛选模式协同Working

### P键 - 导出Static模式
- 所有弹窗内容内联显示
- 方便截图和保存分享
- 使用浏览器"另存为"Features导出

### G键 - Configuration组导航Features

- **Fast访问** - 按G键或点击Top-Right角「📋 导航」按钮打开导航面板
- **智能搜索** - 输入Configuration组名称关键词实时筛选匹配项
- **排除搜索** - 在“排除Configuration组...”输入框中输入关键词，可隐藏不想看到的Configuration组
- **总时长统计** - 导航面板底部显示当前可见Configuration组的累计耗时
- **精准跳转** - 点击搜索结果直接滚动到对应Configuration组位置
- **便捷控制** - 点击Top-Right角开关按钮或按ESC键关闭导航

#### 操作指引
1. **开启导航** - 按 `G` 键或点击页面Top-Right角「📋 导航」按钮
2. **搜索目标** - 在搜索框输入Configuration组名称（Supports部分匹配）
3. **排除干扰** - 在排除框输入关键词，隐藏不关注的Configuration组
4. **Fast跳转** - 从搜索结果列表中选择要查看的Configuration组
5. **关闭面板** - 点击Top-Right角导航开关或按 `ESC` 键退出

---

## 🔧 高级Settings

### URL 参数控制初始状态
您可以通过在网址后添加参数来预设工具的初始状态（所有参数大小写兼容）：

| 参数 | Guide / Instructions | 示例 |
|------|------|------|
| `C=1` | 强制暗色主题（优先级高于Auto 时间判断） | `index.html?C=1` |
| `C=0` | 强制亮色主题 | `index.html?C=0` |
| `LBox=true` | 在电脑端强制显示上传Features按钮区（默认隐藏） | `index.html?LBox=true` |

多个参数可以组合使用，例如：`index.html?C=1&LBox=true`

---

## 🎨 界面Guide / Instructions

### 表格格式
**旧版格式**（默认）
- 单行显示完整任务信息
- 适合详细数据分析

**新版格式(BGI现版格式)**（按USwitch）
- 任务信息分两行显示
- 适合Fast浏览

### 特殊事件检测
工具Auto 检测并标记以下种特殊事件，按错误类型分类：

| 事件类型 | 颜色标记 | 事件Guide / Instructions | 
|----------|----------|----------|
| **Auto 恢复事件** | | |
| Auto Taking Medicine恢复 | 🟢 绿色 | Auto 处理红血状态 |
| Auto 领取派遣任务 | 🟠 橙色 | 正常Features执行 |
| **暂停与中断事件** | | |
| Shortcut Keys暂停 | 🟣 粉色 | 用户手动暂停 |
| 窗口焦点Exception / Error | 🟣 粉色 | 游戏窗口失去焦点 |
| Switch区域Defeat | 🟣 粉色 | 游戏区域SwitchDefeat |
| **用户Configuration错误** | 🔧 | |
| Path文件丢失 | 🔴 红色 | Configuration文件缺失 |
| 未匹配Combat脚本 | 🔴 红色 | Combat脚本Configuration错误 |
| Combat策略错误 | 🔴 红色 | 策略脚本语法错误 |
| 缺少元素采集Character | 🔴 红色 | 队伍缺少对应元素Character |
| 缺少NahidaCharacter | 🔴 红色 | 队伍缺少NahidaCharacter |
| **BGI运行时错误** | 🐛 | |
| 队伍Character识别Defeat | 🔴 红色 | Character识别FeaturesException / Error |
| 未能返回主界面 | 🔴 红色 | 界面导航Defeat |
| Switch PartyDefeat | 🔴 红色 | 队伍SwitchFeaturesException / Error |
| Auto 重启bgi | 🔴 红色 | 调度器任务出现未预期的Exception / Error，Auto 重启bgi |
| **网络与地图问题** | 🌐 | |
| 打开地图Defeat | 🔴 红色 | 地图FeaturesException / Error |
| Teleport Waypoint不存在 | 🔴 红色 | Teleport Waypoint识别问题 |
| 识别大地图Defeat | 🔴 红色 | 地图定位Defeat |
| **用户主动操作** | 👤 | |
| 脚本Exception / Error结束 | 🔴 红色 | 任务被Exception / Error中断 |
| **Other** |  | |
| 缺少脚本指定Character | 蓝紫色 | Path中的简易策略脚本存在着队伍中Nope的Character的提示 |



**计数显示**：同一事件多次发生时会显示次数，如"Shortcut Keys暂停 (3)"

## 📱 移动端适配

### 专用界面
- 触摸友好的大按钮设计
- 自适应屏幕尺寸的布局
- 简化的操作流程

### Features按钮区
6个核心Features按钮：
1. 🌓 主题Switch
2. ⏰ 时间列控制
3. 📊 统计列控制
4. 📦 拾取物控制
5. 📤 导出模式
6. 🔍 Exception / Error任务筛选

## 🔧 技术规格

### Supports格式
- **LogVersion**: BetterGI 0.64.0
- **文件命名**: `better-genshin-impact` 开头
- **日期识别**: Auto 从文件名解析日期
- **编码Supports**: UTF-8 文本格式

### 性能特性
- 💾 客户端本地处理，无数据上传
- 📈 虚拟滚动Supports大数据量
- 🔄 实时响应式布局

## ❓ FAQ

### 数据解析问题
**Q: 为什么有些任务显示"进行中"？**  
A: Log中任务Nope正常结束Recording，可能是脚本被中断。

**Q: 坐标信息为什么有时缺失？**  
A: 只有在卡死或复活前有坐标Recording时才会显示。

**Q: 时间显示Exception / Error怎么办？**  
A: 工具会Auto 处理跨日情况，如仍有问题请检查Log完整性。

### Features使用问题
**Q: 如何分享分析结果？**  
A: 使用P键进入导出模式，然后用浏览器"另存为"保存HTML文件。或截图分享

**Q: 筛选模式如何退出？**  
A: 再次按下H键即可退出筛选模式。

**Q: 弹窗位置乱了怎么办？**  
A: 按R键重置所有弹窗位置，或双击单元格重置单个弹窗。

### 移动端问题
**Q: 手机上传文件Defeat？**  
A: 确保文件命名格式是`better-genshin-impact日期.log`。

**Q: 移动端按钮显示不全？**  
A: 横屏模式可获得更好体验。

## 📋 Changelog
### 20260913
 - 修改重试次数觸發羅輯
 - 補充 41.执行脚本时发生Exception / Error: "Index was outside the bounds of the array."觸發條件
### 20260912
 - 增加錯誤&Other訊息
   - 加入黑名单(鋤地一條龍)
   - 执行地图追踪时候发生错误: "不存在的Character编号"
### 20260909
  - 增加了一些Features
### 20260908
 - 增加錯誤&Other訊息
  - 执行脚本时发生Exception / Error: "Index was outside the bounds of the array."
### 20260904
- M鍵 统计拾取物 Support 全角逗号、英文逗号、空白字符
- 增加錯誤&Other訊息
   - 视角转动超时
### 20260903
- 适配部分Log
 - 检测Route文件格式错误(鋤地一條龍2.13.0)
### 20260830
- 适配部分BGI0.64.0Log
- 38.已达到总运行限时(采集CD管理3.1.0)
### 20260829
 - 修改"Route多次卡死，放弃此Route！Warning"觸發羅輯
 - 适配部分BGI0.64.0Log
 - 队伍資訊增加 是否有開啟光柱拾取模式
### 20260808、20260809、20260824
 - 适配部分BGI0.63.0Log
### 20260801
 - 适配部分Log
   - 检测到复苏按钮，点击 or 复苏完成
### 20260730
 - End坐标Exception / Error，不Recording放入J键隐藏零统计被隐藏關鍵字中
 - 适配部分Log
   - 接近限制时间，等待X分钟

*更早Version包含基础Log解析和显示Features及OtherFeatures*

## 📞 技术Supports

### Precautions / Notes
- 🔒 工具完全在浏览器本地运行，无数据上传
- 📝 仅Supports简体模式下所输出的BetterGILog档
- ⚠️ 分析结果仅供参考，不保证100%准确

---

*最后更新: 2026-09-13*  
*适配 BetterGI 0.64.0 Version*