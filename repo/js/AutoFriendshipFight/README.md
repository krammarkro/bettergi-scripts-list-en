### Author
- [秋云](https://github.com/physligl)（原Author）
- Volcano
- 莫酱

> Auto 化刷取CharacterFriendship度的脚本，SupportsTreasure Hoarder、愚人众、鳄鱼等敌人类型（Floating Fungi与雷Cicin Mage为测试项）。通过Auto 触发和完成突发任务来获得Friendship度经验。

### 目录
- [Features简介](#Features简介)
- [敌人类型](#敌人类型)
- [FastStarting Up](#FastStarting Up)
- [运行流程](#运行流程)
- [FAQ](#FAQ)
- [文件结构](#文件结构)
- [Precautions / Notes](#Precautions / Notes)
- [Changelog](#Changelog)

### Features简介

Auto 化刷取CharacterFriendship度的脚本，SupportsTreasure Hoarder、愚人众、鳄鱼等敌人类型（Floating Fungi与雷Cicin Mage为测试项）。通过Auto 触发和完成突发任务来获得Friendship度经验。



- **日限制**: 每日最多获得10次Friendship度奖励，50次任务触发，在别的地方触发过Friendship任务会扣减相应次数。
- **循环控制**: 运行次数由 `runTimes` 控制；若未触发任务或Happy提前终止条件会Auto 结束。
- **平均时长**: 每次循环约1分钟，效率高时可以达到40秒单次循环。
- **成功率**: Configuration正确的情况下接近98%，有概率丢失第一次Friendship任务。

### 敌人类型

#### Treasure Hoarder
| 属性 | 详情 |
|------|------|
| **触发任务** | 岛上无贼 - 消灭鬼鬼祟祟的Treasure Hoarder |
| **活动地区** | Inazuma地区 |
| **敌人强度** | ⭐⭐⭐ (中等) |
| **特殊Features** | （可选）Supports清理原住民（Hilichurl） |

#### 愚人众&Hilichurl&Treasure Hoarder
| 属性 | 详情 |
|------|------|
| **触发任务** | 买卖不成正义存 - 打倒愚人众与镀金旅团<br>禁止危险运输！ - 打倒所有Treasure Hoarder<br>Hilichurl今晚的伙食 - 打倒所有Hilichurl |
| **活动地区** | Sumeru地区 |
| **敌人强度** | ⭐⭐⭐⭐ (较高) |


#### 鳄鱼
| 属性 | 详情 |
|------|------|
| **触发任务** | 张牙舞爪的恶党 - 打倒所有鳄鱼 |
| **活动地区** | Sumeru地区 |
| **敌人强度** | ⭐⭐ (较低) |
### FastStarting Up
#### 环境准备
✅ 安装 BetterGI，Version大于 0.44.7
✅ 订阅脚本并添加至调度器

#### Floating Fungi & 雷Cicin Mage
属于测试Version，暂时并Unstable，可以进行测试，但不建议作为日常脚本使用。

#### 调度器Configuration
- **地图追踪行走Configuration**:
  - ✅ 勾选"只在Teleport Waypoint时回复"
  - ✅ 勾选"允许在JsScript使用"
  - ✅ 勾选"覆盖JS中的Auto CombatConfiguration"

- **CombatConfiguration**
  - **Combat策略**: 根据队伍选择或者制定合适的Combat策略文件
  - **练度要求**: 建议较高练度，纯Friendship队可能无法击败敌人
  - **重要Settings**:
    - 默认：❌ 关闭"Auto 检测Combat结束"
    - 若勾选“禁用异步Combat（更Stable）”：✅ 需要开启并正确Configuration"Auto 检测Combat结束"（对所有敌人生效）
- **Recommended队伍Configuration**
 > 基于社区测试的EfficientCharacterRecommended，Other效率高的Character欢迎通过 pull request 添加到本文档，需附带理由和演示视频。

| Character | 优先级 | 特点 | Precautions / Notes |
|------|--------|------|----------|
| **Neuvillette** | ⭐⭐⭐⭐⭐ | 群友测试效率最高 | 输出Stable，适合Auto Combat |
| **Citlali** | ⭐⭐⭐⭐ | 带盾，后台冰冻结敌人 | 提供生存保障 |
| **Kaedehara Kazuha** | ⭐⭐⭐⭐ | 拾取材料，扩散伤害 | 增加收益效率 |
| **Furina** | ⭐⭐⭐ | 后台输出 | 生存压力较大 |
| **Zhongli** | ⭐⭐⭐ | 提供护盾 | Combat策略中E技能应左右释放 |
#### **脚本Settings**
> 通过调度器脚本右键-修改JS自定义Configuration

   - 禁用Auto 拾取实时任务（`disablePickup`）
     - 不勾选：启用Auto 拾取（默认）
     - 勾选：禁用Auto 拾取
   - 敌人类型: Supports"Treasure Hoarder"、"愚人众"、"鳄鱼"、"Floating Fungi"、"雷Cicin Mage"
   - 运行次数:
     - 请输入正整数（默认10次）
     - 刷Friendship通常建议 10 次以内，避免超过每日奖励上限
   - 清理Hilichurl超时时间（`qiuQiuRen`，秒）
     - 默认 0（不执行）
     - 仅Treasure Hoarder有效，填入大于 0 的秒数后会先执行清理阶段
   - 队伍名称: 
     - 填入您的Combat队伍名称
     - 不填默认当前队伍
   - OCR超时:
    - OCR检测超时时间（默认10秒）
    - 过短可能识别Defeat导致结束任务
    - 过长则会长时间检测导致等待时间过长
    - Recommended保持默认值
   - Combat超时: 
    - 单次Combat超时时间（默认120秒）
    - Combat超时会直接取消任务，因此不建议过短
    - 脚本会Auto 检测任务结束，识别精度很高
   - 禁用异步Combat（更Stable；需Configuration“Combat结束检测”；对所有敌人生效）
    - 开启后统一走同步Combat执行分支
    - 关闭时走异步Combat + OCR 判定分支

#### 一键运行
Configuration完成后，直接运行脚本即可Starting UpAuto 刷取Friendship度。


#### 高级Settings
- **清理原住民**: 仅Treasure Hoarder模式有效，清理Hilichurl
- **卡时间模式**: Supports按日期周期运行

### 运行流程

1. **队伍Switch**: Auto Switch到指定队伍
2. **准备阶段**: 
   - Treasure Hoarder: (可选) 清理Hilichurl → Go to触发点
   - 愚人众: 直接Go to触发点
3. **任务检测**: 使用OCR检测突发任务触发
4. **Combat执行**: Auto 导航到Combat点并Starting UpCombat
5. **结果判定**: 检测Combat结果并Recording
6. **循环执行**: 重复上述流程直到完成设定次数或者检测到任务未触发


### FAQ

#### 重要提醒
- 脚本运行时请勿手动操作游戏

#### FAQ解答

##### Q: 为什么Combat策略Nope生效或CombatDefeat率较高？
**A**: 检查以下几点：
- 是否正确Settings了Combat策略
- Combat策略是否适合当前队伍
- 队伍练度是否足够
- 是否正确勾选了"覆盖JS中的Auto CombatConfiguration"


##### Q: OCR超时但是任务已经触发？
**A**: 
- 尝试提高 OCR 超时时间
- 如果Observing到触发任务时，Left SideNope任务文字，则游戏中关闭任务Focused模式

##### Q: 如何选择合适的敌人类型？
**A**:
- **Treasure Hoarder**: 适合中等练度队伍，敌人相对较弱
- **愚人众**: 需要高练度队伍，怪物强度相对较高

##### Q: 脚本运行中断怎么办？
**A**:
- 检查是否有手动操作游戏
- 查看Log确定中断原因
- 重新运行脚本
- 若仍然未恢复，提交 issue

##### Q: 脚本卡在某个步骤不动怎么办？
**A**:
- 确认是否卡在了复活界面
- 重启脚本并检查 BetterGI 状态
- 若仍然未恢复，提交 issue

##### Q: 如何选择Treasure Hoarder还是愚人众？
**A**:
- **新手Recommended**: 选择Treasure Hoarder，敌人较弱，容错率高
- **高练度队伍**: 选择愚人众，效率更高
- **Friendship度优先**: 两者都可以，选择队伍更适合的类型

##### Q: Combat策略如何Configuration？
**A**:
- 查阅 BetterGI 文档

##### Q: 为什么任务触发Defeat？
**A**:
- 检查是否已达到每日任务触发上限
- 尝试手动触发

##### Q: 队伍SwitchDefeat怎么办？
**A**:
- 确认队伍名称填写正确（建议四字中文）

##### Q: 脚本运行速度慢怎么办？
**A**:
- 降低OCR超时时间（但不要过短）
- 优化Combat策略，减少不必要的等待
- 确保BetterGIVersion为最新
- 检查计算机性能和网络状况
- 提高计算机Configuration

##### Q: 如何备份和恢复Configuration？
**A**:
- Configuration保存在调度器Configuration文件中
- 可以手动备份该文件，当然建议直接备份 `User` 文件夹
- 重装后将备份文件复制回原位置即可恢复

> 💡 如遇Other问题，请在 GitHub 上提出 issue

### 文件结构

- `main.js`: 主要脚本逻辑
- `settings.json`: Configuration文件
- `assets/AutoPath/`: Path文件目录
  - `Treasure Hoarder-准备.json`: Treasure Hoarder准备阶段Path，清理Hilichurl
  - `Treasure Hoarder-触发点.json`: Treasure Hoarder触发点Path
  - `Treasure Hoarder-Combat点.json`: Treasure HoarderCombat点Path
  - `愚人众-准备.json`: 愚人众准备阶段Path，从Teleport Waypoint到触发点
  - `愚人众-触发点.json`: 愚人众触发点Path
  - `愚人众-Combat点.json`: 愚人众Combat点Path

### Precautions / Notes

#### 使用须知
- **仅供Learning交流**: 本脚本仅用于技术研究和Learning交流
- **风险自担**: 使用Auto 化脚本存在一定风险，请谨慎使用
- **适度使用**: 建议合理安排游戏时间，避免过度依赖Auto 化

#### 安全建议
- **备份存档**: 使用前建议备份游戏存档数据
- **监督运行**: 运行期间建议保持关注，及时处理Exception / Error情况
- **Version更新**: 及时更新 BetterGI 和脚本到最新Version
- **社区反馈**: 遇到问题及时向社区反馈，帮助改进脚本

### Changelog

| Version | 更新内容 | 
|------|----------|
| **v2.0.0** | `main.js` 重构Version：重点修复 V8 弹窗报错与内存溢出问题；统一敌人Configuration驱动与主循环流程；“禁用异步Combat”明确为对所有敌人生效；移除卡时间Features及相关Configuration入口 |
| **v1.5.3** | Stable性提升：资源释放更完整；Treasure Hoarder游泳统计仅在Treasure Hoarder启用；“禁用异步Combat”增加超时Protection避免卡死；SettingsGuide / Instructions更易懂 |
| **v1.4.2** | 新增拾取模式，能选择不拾取 | 
| **v1.3** | 新增愚人众Supports，优化敌人类型Switch | 
| **v1.2** | Combat触发检测，异步检测Combat结束 | 
| **v1.1** | Treasure Hoarder重登Features优化，卡时间Supports |
| **v1.0** | 基础Treasure HoarderFriendship度刷取Features | 

---

### 贡献指南
欢迎提交 Pull Request 来改进此脚本！请遵循以下指南：

#### 代码贡献
- **Features改进**: 新增Features、性能优化、bug修复
- **文档完善**: 改进README、添加注释、使用指南
- **测试验证**: 提供测试用例、兼容性验证

#### 提交规范
- 清晰的提交信息描述
- 详细的PRGuide / Instructions和测试结果
- 遵循现有代码风格
- 避免在同一个提交中格式化代码

### 问题反馈
遇到问题请在 GitHub 上提出 issue，包含以下信息：
- 详细的错误描述和复现步骤
- 相关Log截图或错误信息
- 使用的BetterGIVersion和游戏环境
- 脚本Configuration参数

### 社区Supports
- 📖 **文档**: 查看完整文档和教程
- 🐛 **报告问题**: 通过Issues报告bug和建议
- 🤝 **贡献代码**: 通过Pull Request贡献代码

> 💝 **Thank You所有为此项目做出贡献的开发者和测试者！**

> 🌟 **如果这个脚本对您有帮助，请给项目点个星标Supports！**
