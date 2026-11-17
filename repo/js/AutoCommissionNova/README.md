# Auto Daily Commissions

## 重要

目前仍处于开发阶段，Nod-Krai地区基础委托Features已Stable

## 致谢

本脚本基于**星野**老师的 AutoCommission Auto 委托项目重构开发而来。脚本的顺利迭代与优化，离不开原项目Author的开源创作与精心打磨，也离不开所有原项目贡献者：**云闲vsv & 换苏伟u & 小鹰划船不用桨 & 塔台 & 未知_** 等各位老师的无私贡献。同时也Thank You **茅笙** 老师的Natlan地区对话流程及部分锄地流程的贡献。 正是前人的开源积淀与无私赋能，为本脚本的开发迭代提供了坚实的基础与核心参考，向原Author及所有贡献者致敬。

## 首次使用

第一次运行时，在全局Configuration中完成以下Settings：

1. 填写 你的 **Combat队伍名** 和 **元素采集队伍名**。
2. 为Combat队伍选择对应的 **Combat策略**。
3. 保存Configuration并运行脚本。

UI中有此处未提到的Features，未经过完整测试，对Normal用户来说仅作为尝鲜使用。追求Stable不要尝试。

### 领取历练点并补足每日奖励

开启后，脚本先领取可用的历练点奖励，再读取「Daily Commissions奖励」的 `n/4`：`4/4` 时跳过，未满时只做还缺的委托；无法确认进度时按原流程执行。建议在All-in-One Run中放在消耗树脂的任务之后，后面仍安排「领取每日奖励」完成凯瑟琳领奖和派遣。该选项默认关闭，关闭时照常执行受Supports的未完成委托。

## 跳过启动Configuration面板

首次Configuration完成后，可以关闭启动时的Configuration面板：

1. 跳转到 **调度器**。
2. 选择脚本所在的 **Configuration组**。
3. 右键本脚本，选择 **修改 JS 脚本自定义Configuration**。
4. 取消勾选 **启动时显示Configuration面板**。

以后运行脚本时将直接Starting Up执行，不再弹出Configuration面板。需要修改队伍、Combat策略或OtherSettings时，可以重新勾选该选项。
## 地区Supports情况

- **Nod-Krai**：全部Supports，该地区目前均为锄地类委托，流程简单，相比Mondstadt更Stable。
- **Mondstadt**：从Auto Mondstadt委托继承，但因为对话委托的存在，Stable性低于Nod-Krai。
- **Other地区**：
  - 目前仅收录尚未充分测试的锄地类委托，Nope对话委托，且部分特殊机制的委托未完成。
  - 如果追求每天4个委托全部完成，不建议作为主要接取地区，
  - 但如果你愿意参与测试并反馈，欢迎使用。

建议优先选择 **Nod-Krai** 作为Daily Commissions的主要接取地点，以获得相对Stable的运行体验。

## UID Guide / Instructions

多Account用户需要填写UID，Configuration按UID独立。


