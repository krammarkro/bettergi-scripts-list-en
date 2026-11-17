# 原神Auto 委托脚本

## 项目简介
这是一套基于 BetterGI 的Auto 化脚本，可帮助Auto 完成《原神》的Daily Commissions任务。脚本能Auto 识别委托内容、追踪任务Path，并Supports智能对话选项处理。
目前项目正处于急需人手,有意者请加QQ群（会在地图上标点或按按钮即可）。

## FastStarting Up

### 第一步：添加脚本到调度器
1. 订阅本脚本
2. 在将脚本添加至调度器**不要直接运行**

### 第二步：Configuration脚本Settings
右键点击脚本，选择「修改 JS 自定义Configuration」：
- **不要勾选「跳过委托识别」**（这是给开发者设计的Features）
- 「Switch Party不Go toStatue of The Seven」及「完成后不去安全地点」根据个人偏好Settings
- Settings你的Combat队伍名称（留空表示不Switch Party）
- Settings元素采集队伍名称（队伍需要包含风、火、水元素Character和柱子对策）

### 第三步：Configuration调度器Settings
- Combat超时设为40-60秒
- 最好关闭Auto Combat-Combat后Auto 拾取掉落物，避免浪费大量时间
![](Configuration组Configuration参考.png)


### 第四步：运行脚本
关闭弹窗后后直接运行即可Starting UpAuto 完成Daily Commissions。

## 队伍Configuration建议

### 采集队伍RecommendedConfiguration
采集队伍需要包含以下元素Character：
- **风元素**：必备采集元素用于特殊委托
- **火元素**：必备采集元素
- **水元素**：必备采集元素
- **柱子对策**：用于特殊委托打3+3柱子

**RecommendedCharacter组合**：Zhongli + Sucrose + Bennett + Barbara

### Supports的Character列表
| 元素 | Character |
|------|------|
| 风元素 | Sucrose、Shikanoin Heizou、Wanderer、Xianyun、Lan Yan、Kaedehara Kazuha、Faruzan、Lynette、Venti、琴、Sayu |
| 火元素 | Yanfei、Diluc、Klee、Bennett、Xiangling、Thoma、Hu Tao、Dehya、Chevreuse、Xinyan、Lyney、Yoimiya |
| 水元素 | Barbara、Mona、Sangonomiya Kokomi、Mualani、Neuvillette、Furina、Nilou、坎蒂斯、Xingqiu、Kamisato Ayato |
| 3+3柱子对策 | Zhongli、Kaedehara Kazuha、奶奶、Neuvillette（理论，暂未Supports）、Xiangling（理论，暂未Supports） |

## FAQ解答

### Q1: 为什么打开冒险之证脚本就出错？
请检查BGIShortcut Keys-停止当前脚本/Other工具Shortcut Keys是否绑到F1，如果是请换一个按键，F1是打开冒险之证的Shortcut Keys。

### Q2: 为什么不打怪？
- 确保已正确ConfigurationCombat策略[Combat策略编写文档](https://bettergi.com/feats/task/domain.html)
- 直接抄我的也可以，脚本仓库-Combat脚本搜Auto 委托，里面的都包成功

### Q3: 为什么打不到塔上的怪？
- **你带Furina了吗，Nope快去带呀**
- 还有一些真打不到，请将Combat超时设为40-60秒（看个人练度）

### Q4: 为什么有的委托无法完成？
- 先看BGI文档能不能解决[BGI文档](https://bettergi.com/doc.html)
- Combat委托无法完成99%都It's You配队问题**你带AOE了吗**
- 还有问题请将 BetterGI/log/ 目录下当天的Log和委托任务截图反馈给Author，以便排查问题。


## 开发指南
对话委托开发文档[AutoCommission 标准对话委托制作指南](https://cnb.cool/bettergi/bettergi-scripts-list/-/tree/main/repo/js/AutoCommission/对话委托制作方法.md)。


## 反馈方法
- 1.加QQ群1053392753反馈
- 2.发送截图,Log给3302871403@qq.com
- 3.BGI QQ频道@星野

## Changelog
### 当前Version：0.98.18 (2026-06-04)
- 修复已知问题 (2026-06-04 15:10:23 UTC)

### 上一Version：0.98.17 (2026-06-04)
- **委托流程修复与补充**：
  - *语言交流*、*诗歌交流*、*钥匙是易丢品*：补充多个地区的对话选项和流程Configuration，修正重试后地点更新逻辑，避免沿用上一次Defeat识别的委托地点。
  - *Surprised大礼*：优化Searching乔玛丽的Path，降低走过头导致交互Defeat的概率。
  - *西风骑士的基础知识*、*餐品订单*：优化流程中的交互与Path细节。
  - *邪恶的扩张*：将区域名从「Brightcrown Canyon」更正为「Brightcrown Mountains」。
- **识别与执行Stable性优化**：
  - 优化靠近 NPC 后小概率未出现对话选项时的处理。
  - 大地图位置识别改为投票机制，提升坐标判断Stable性。
  - 更新 step fallback 加载逻辑，移除冗余和易误导Log。

### 上一Version：0.98.16 (2026-01-30)
- **委托流程更新**：
  - *新的风暴尚未出现*：区域从「Stormbearer Point」调整为「望风海岸」，新增Go toStormbearer Point塔楼顶部的NormalPath和 TP Path。
  - 爬塔流程增加三次重试机会，减少偶发寻路或攀爬Defeat。
- 删除冗余流程文件，修正执行流程中参数数量不一致的问题。

### 上一Version：0.98.15 (2026-01-20)
- **委托识别优化**：
  - 新增委托名与地点名 OCR 结果校正，降低识别错误导致无法匹配流程的概率。
  - 保存识别到的委托任务时，避免任务地点被同一天上次执行Defeat后的地点覆盖。
- **流程与兼容性调整**：
  - 适配 BetterGI 本体 AutoSkip 相关改动。
  - 修正 *报答神明的方式* 的流程文件名。
  - 清理 *艾伯特先生别再冲了*、*艾琳，未来的骑士* 的重复/误命名流程目录。
- 修复Auto 同步Working流中Version号不同步的问题，并调整 PR 模板内容。

### 上一Version：0.98.14 (2026-01-07)
- **新增更新提示**：新增Version检查模块，启动时可提示当前脚本是否需要更新。
- **地图与 OCR 识别优化**：
  - 调整大地图缩放级别，修复部分委托从大地图获取坐标时报That's Wrong问题。
  - 修复委托描述检测 step 的参数检查逻辑。
  - 增加 OCR 全部结果的 debug Log输出，便于排查识别问题。
  - 增高对话选项 OCR 识别范围，减少选项较多时漏识别的问题。
- **委托流程修复**：
  - *钥匙是易丢品*：修复Dawn Winery支线位置偏移问题。
  - *Surprised大礼*：补充对话优先选项。
  - *语言交流*：根据后续回退结果，修正区域分支归属，避免错误匹配。
- **Auto 同步流程**：新增/完善同步到脚本列表仓库并创建 PR 的Working流，Supports PR 正文Showing Off提交历史。

### 上一Version：0.98.12 (2025-12-24)
- 新增 `.gitattributes`，统一仓库换行符处理。
- 新增Auto 同步代码并创建 PR 的 GitHub Actions Working流。
- *钥匙是易丢品*：更新Dawn Winery流程Configuration。
- 更新 README 描述与Version相关Configuration。

### 上一Version：0.98.11 (2025-12-21)
- **委托流程修复**：
  - *语言交流*：修正地图追踪参数和区域分支Configuration。
  - *Surprised大礼*：补充对话优先选项。
  - *愿鲜花气息逗留*：解除 ban 状态，恢复流程可用性。
- **执行与对话逻辑优化**：
  - 删除冗余参数，修正对话 icon 识别范围。
  - 同步 BetterGI 主仓强制 dispose 相关改动。
  - 删除关闭商店 step，并同步更新相关委托流程。
- 更新 README、SettingsGuide / Instructions和Version号。

### 上一Version：0.98.10 (2025-10-20)
- **新增委托流程Supports**：
  - 向冬日回归
- **委托流程更新，包括**：
  - *圆滚滚的大团骚乱*
    - 风Character驱散Exception / Error点后Switch Party再进入Combat
  - *说到做到*
    - Path更新
  - *愿鲜花气息逗留* 
    - 流程更新，现在能正确的循着踪迹Searching包裹
  - *父亲能做的事*
    - Path更新，现在可以正确的抵达教堂
  - *应急补给*
    - Supports与行走中的NPC对话
  - *一个男孩的去信*
    - 修复特定条件下与杜拉夫对话Defeat的问题
- 对话模块
  - 在对话中选项Nope命中白名单，且Nope含退出图标与气泡图标的选项，默认点击最后一个选项。

### 上一Version：0.98.7 (2025-09-29)
- 大幅优化委托流程执行效率
- 新增"把信件送给莎拉"委托Auto 化Supports
- 完善"鸽子习惯一去不回"系列委托流程
- 优化13个委托流程Configuration文件，提升执行精确度
- 重构对话处理器代码逻辑，简化维护
- 改进Combat委托追踪和对话识别机制
- 总计修改16个文件（新增761行，删除505行）

### 上一Version：0.98.6
- 新增图像识别工具库（image_utils.js）
- 新增对话处理器Features增强
- 新增商店关闭Features（close-store.js）
- 新增多个委托流程Supports，包括：
  - 大量新的对话委托
  - 多个新的寻路Path
  - 紧急补给系列委托
  - 各地区特殊委托优化
- 优化常数Configuration和主要逻辑
- 修复大量已知问题
- 总计修改105个文件

### 上一Version：0.98.5
- 懒得统计了修改了80+个文件

### 上一Version：0.98.4
- 模块化架构完成，新增 18 个对话委托、113 条流程

### 旧Version：0.98.2
- 新增 83 Character头像识别，8 个对话委托


### 旧Version：0.97
- 修复已知问题
- 完成了更多对话委托

### 旧Version：0.96
- 优化对话委托处理逻辑
- 优化Combat委托处理逻辑
- 增强NPC对话选项智能识别
- Supports自定义对话优先选项
- 新增NPC白名单Features，提高交互精确度
- 完善对话委托文档，增加JSON和简易格式Guide / Instructions

### 旧Version：0.95
- 完成了对话委托Features实现

### 旧Version：0.94.1
- 修复攀High Risk险问题
- 完成了更多对话委托
- 修复委托不存在

### 旧Version：0.94
- 修复攀High Risk险问题
- 新建了对话委托的文件夹

### 旧Version：0.93
- 修复已知问题

### 旧Version：0.92
- 修复部分Path命名错误
- 修复第4个委托识别Defeat

### 旧Version：0.91
- 修改寻路Features改为两条Path都尝试一遍
- 修复委托已完成退出错误
- 增加输入检测

### 旧Version：0.90
- 实现基本的委托识别Features
- Supports委托地点OCR识别
- 基础的委托Path追踪Features


