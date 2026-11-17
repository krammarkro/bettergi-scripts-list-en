# Auto 幽境危战Precautions / Notes

## 零、前言

- 当前文档处于测试阶段，Precautions / Notes可能尚不完善，敬请谅解。
- 如发现BUG，请通过QQ：119996800联系我们，您的反馈将非常受欢迎。
- 本脚本基于地脉花和BossAll-in-One Run脚本进行改造。
- 脚本仅供娱乐使用，请在下载后24小时内删除。

## 一、省流Precautions / Notes

1. **使用前准备**：
   - 请在`<<幽境危战>>`中Configuration好Combat队伍。
2. **黑名单建议**：
   - 根目录下有文件内含建议加入`Auto 拾取黑名单`的名称，请检查并添加。
3. **Combat实力**：
   - 请确保队伍具备足够的Combat实力，当前Version在CombatDefeat或执行错误，只会重试`一次`。
4. **Auto 拾取Features**：
   - 为避免不必要的干扰，建议关闭Auto 拾取Features。

## 二、Configuration简介

1. **Artifacts奖励**：
   - 默认Settings下，脚本不会修改Artifacts奖励。

2. **BossChallenge关卡选择**：
   - 必填项：请从上往下选择第几个BossChallenge关卡`（1至3）`，否则脚本将无法执行。

3. **Challenge次数**：
   - 默认Settings为`15`次，期间若树脂耗尽，脚本将Auto 结束。

4. **树脂顺序设定**：
   - 使用`/`隔开数字来设定树脂使用顺序，如`1/2`表示先使用Condensed Resin，再使用原粹树脂。
   - 树脂类型对应关系：
     - 1 = Condensed Resin
     - 2 = 原粹树脂
     - 3 = 脆弱树脂
     - 4 = 须臾树脂
   - 默认Settings：`1/2`，表示先使用Condensed Resin，再使用原粹树脂，不填的不使用"。

5. **最长Combat超时时间**：
   - 默认Settings为`240`秒，一般情况下无需修改。

6. **Starting UpCombat后的移动时间**：
   - 默认Settings为`1`秒（Note单位为`秒`），由于CombatStarting Up位置离Boss较远，请根据实际情况设定，一般情况下默认Settings即可。

## 三、更新Guide / Instructions

### v.1.0Version（20250627）

- **Features**：脚本发布。

### v.1.1Version

- **备注**：此Version信息被省略。

### v.1.2Version（20250627）

- **新增Features**：
  1. 添加Artifacts`奖励选择`Features。
  2. 添加Auto 选择`难度`Features。
- **优化**：
  1. 优化逻辑处理。
  2. 加大Combat完成识别区域。

### v.1.3Version（20250628）

- **新增Features**：
  1. 添加`Auto 重试`，CombatDefeat或执行错误会`重试一次`。
- **优化**：
  2. 优化退出点击时序和逻辑。
  3. 优化进入Domain后向前走的逻辑。
  4. 优化LOG输出显示内容。
- **修复**
  1. 修复默认状态下，选择长夜套的BUG。

### v.1.4Version（20250629）

- **新增Features**：
  1. 添加领奖后的树脂识别，不足时退出Domain，防止多打一次。
- **优化**：
  1. 优化`再次Challenge`Challenge的点击逻辑，添加重试。
  2. 优化相关Auto 拾取代码。
  3. 优化`难度选择`和`Artifacts选择`的识别范围。

  ### v.1.5Version（20250630）

- **新增Features**：
  1. Auto CombatDefeat原地`重试2次`，Defeat后再退出Domain重试。
- **优化**：
  1. 优化`LOG`显示。
  2. 优化`完全Nope树脂`情况弹窗提示处理。
  3. 优化删除拾取`黑名单`文件（0.47.0后不会乱触发了）。
  4. 优化各种`异常状态`的退出处理方法。
  5. 优化当有须臾树脂时，脆弱树脂不显示时的处理。

  ### v.1.6Version：20250702

- **优化**：
1. 优化没找到地脉花领奖的超时退出处理。
2. 优化树脂识别OCR区域。
3. 优化LOG和代码写法和整理。



