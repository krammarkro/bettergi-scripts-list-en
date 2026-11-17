# Auto 幽境危战Precautions / Notes

## 零、前言

- 本代码仅供娱乐Learning，下载请24小时内删除，禁止用于商业行为，如有BUG，非常欢迎请到测试群反馈或Q119996800。
- 本脚本基于地脉花和BossAll-in-One Run脚本进行改造。

## 一、省流Precautions / Notes

1. **使用前准备**：
   - 请在`<<幽境危战>>`中Configuration好Combat队伍。
3. **Combat实力**：
   - 请确保队伍具备足够的Combat实力，当前Version在CombatDefeat或执行错误，只会重试`一次`。

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
   - 默认Settings为`240`秒，一般情况下无需修改，建议和Configuration组中的Combat超时一致。

6. **Starting UpCombat后的移动时间**：
   - 默认Settings为`1`秒（Note单位为`秒`），由于CombatStarting Up位置离Boss较远，请根据实际情况设定，一般情况下默认Settings即可。

7. **Combat策略选择**：
   - `使用BetterGICombatConfiguration(下方指定策略无效)`：当Configuration为当前选项时，bgi首先会去`调度器→Configuration组→Settings→CombatConfiguration`中获取相应信息，如果CombatSettings未启用，则会去`独立任务→Auto Combat`中获取
   
   - `指定Combat策略`：在Combat策略名称栏中填写文件名（后缀.txt加不加都行，建议不加）,如 `四神队(进阶版)`，实际查找 `User/AutoFight/四神队(进阶版).txt`,如果位于子目录：例如`AutoFight/群友分享/四神队(进阶版).txt`则填写`群友分享/四神队(进阶版)`）。

   - 策略文件存放位置：`BetterGI/User/AutoFight/`

8. **指定Combat策略名称**：
   - 当选择`指定Combat策略`时，填写具体的策略文件

9. **爆发期时间缓存(测试)**：
  - 在启用了新版寻路之后，会顺路识别结束时间信息，在一定时间内启动脚本就无需检查直接结束
  - 这Features目前不太完善，他暂时还处理不了两个Version之间的间隙
  - 当不启用新版寻路时，这个Features是不可用的，因为执行过程中Nope能识别时间的地方，但因为不涉及严重错误，所以只做了Warning

## 问题排查

<details>
<summary>未匹配到任何Combat脚本</summary>
一般是CombatConfiguration文件有错误导致的

- 使用BetterGICombatConfiguration
  1. 首先检查`Configuration组→Settings→CombatConfiguration`检查Combat策略是否正确
  2. 如果`Configuration组→Settings→CombatConfiguration`未打开则Go to`独立任务→Auto Combat`继续检查
  3. 如果仍然有问题则`独立任务→Auto Combat`手动启动Combat（Configuration好你需要的Combat策略）手动Switch好队伍，启动测试，如果不能运行，则参照bgi的文档进行问题排查

- 指定Combat策略
  1. 查看Settings的Combat策略是否正确
  2. 部分文件名含有.txt是不能使用的(不是指后缀)，例如.txtaa.txt(或者aa.txt.txt)程序处理完之后会变成aa.txt，导致无法指向原有的文件

</details>
<details>
<summary>Combat策略文件不存在</summary>

- 使用BetterGICombatConfiguration
  1. 首先检查`Configuration组→Settings→CombatConfiguration`，查看CombatConfiguration开关是否已经打开，如果打开，检查Combat策略是否正确
  2. 如果未打开则Go to`独立任务→Auto Combat`继续检查
  3. 如果仍然有问题则`独立任务→Auto Combat`手动启动Combat（Configuration好你需要的Combat策略）手动Switch好队伍，启动测试，如果不能运行，则参照bgi的文档进行问题排查


- 指定Combat策略
  1. 查看Settings的Combat策略Path是否正确
  2. 部分文件名含有.txt是不能使用的(不是指后缀)，例如.txtaa.txt(或者aa.txt.txt)程序处理完之后会变成aa.txt，导致无法指向原有的文件

</details>


## 三、更新Guide / Instructions
### v.2.5Version：20260826

- **新Features**：
1. 添加新版寻路Features（有更快的识别速度），默认启用，Defeat时Auto 回退到旧版
2. 添加开发模式开关，开启后Nope, Not In爆发期也会继续执行，还能顺便在OCR时，把识别的位置用红框绘制出来,方便Debug
3. 添加爆发期时间缓存Features（⚠测试Features），缓存爆发期/紊乱平息的时间信息，下次运行时跳过OCR检测直接判断状态 ~~(写完才发现限制挺大的，如果Nope反馈有误识别问题的话当一个效率增强的手段应该也还可以)~~

- **优化**：
1. 优化了Combat的错误处理，现在严重错误会立马抛出并退出脚本，不会原地罚站等待240秒超时了

## 三、更新Guide / Instructions
### v.2.4Version：20260820

- **优化**：
1. 适配7.0，添加了新Artifacts的识别。
### v.2.3Version：20260704

- **优化**：
1. 处理上一个VersionCombat策略的转义问题（bettergi已经处理了这个问题，不再无脑转换），同时处理了.txt后缀，现在加不加都行
2. 增加了新的爆发期检测行为,使其能够识别紊乱平息界面，活动还没Starting Up时下不会再傻等20秒了
3. 优化文档描述，修正部分Configuration名称
### v.2.2Version：20260529

- **新Features**：
1. 添加Combat策略ConfigurationFeatures，Supports指定自定义Combat策略文件

- **优化**：
1. 完善Combat执行逻辑，增加Exception / Error处理

### v.2.1Version：20250918

- **优化**：
1. 改用Normal模板匹配Condensed Resin。
2. 适配6.0奖励领取页面，添加Primogems使用选项，添加新Artifacts的选择。
3. 添加选择队伍Features。

### v.2.0Version：20250830

- **优化**：
1. 改用模板匹配进行Condensed Resin识别，使用颜色遮罩模板，全脚本要求BGIVersion提高到0.47.1。
2. 针对2K和4K分辨率，降低匹配度要求，提高识别精度。

### v.1.9Version：20250828

- **新Features**：

- **优化**：
1. 优化内存释放。
2. 优化JSSettings显示。

### v.1.8Version：20250809

- **新Features**：

- **优化**：
1. 进入各种页面的等待时间增加，防止卡顿报错。
2. 树脂识别错误纠正处理。


- **新Features**：

- **优化**：
1. 进入选择页面时，判断是否在爆发期。
2. 更改进入Domain的判断，避免因为聊天按键被改导致判断错误。


### v.1.7Version：20250807

- **新Features**：

- **优化**：
1. 进入选择页面时，判断是否在爆发期。
2. 更改进入Domain的判断，避免因为聊天按键被改导致判断错误。

### v.1.6Version：20250702

- **优化**：
  1. 优化没找到地脉花领奖的超时退出处理。
  2. 优化树脂识别OCR区域。
  3. 优化LOG和代码写法和整理。

### v.1.5Version（20250630）

- **新增Features**：
  1. Auto CombatDefeat原地`重试2次`，Defeat后再退出Domain重试。
- **优化**：
  1. 优化`LOG`显示。
  2. 优化`完全Nope树脂`情况弹窗提示处理。
  3. 优化删除拾取`黑名单`文件（0.47.0后不会乱触发了）。
  4. 优化各种`Exception / Error状态`的退出处理方法。
  5. 优化当有须臾树脂时，脆弱树脂不显示时的处理。

### v.1.4Version（20250629）

- **新增Features**：
  1. 添加领奖后的树脂识别，不足时退出Domain，防止多打一次。
- **优化**：
  1. 优化`再次Challenge`Challenge的点击逻辑，添加重试。
  2. 优化相关Auto 拾取代码。
  3. 优化`难度选择`和`Artifacts选择`的识别范围。

### v.1.3Version（20250628）

- **新增Features**：
  1. 添加`Auto 重试`，CombatDefeat或执行错误会`重试一次`。
- **优化**：
  2. 优化退出点击时序和逻辑。
  3. 优化进入Domain后向前走的逻辑。
  4. 优化LOG输出显示内容。
- **修复**
  1. 修复默认状态下，选择长夜套的BUG。

### v.1.2Version（20250627）

- **新增Features**：
  1. 添加Artifacts`奖励选择`Features。
  2. 添加Auto 选择`难度`Features。
- **优化**：
  1. 优化逻辑处理。
  2. 加大Combat完成识别区域。

### v.1.1Version

- **备注**：此Version信息被省略。

### v.1.0Version（20250627）

- **Features**：脚本发布。
