# 使用历练点完成Daily Commissions脚本使用指南

## Features概述

1. **队伍管理**：
   - Auto Switch到指定队伍（Friendship队伍）
   - 可选择是否传送至Statue of The SevenSwitch Party
   - SupportsSettings移动专用队伍：若Friendship队伍中包含 BGI 尚未识别的Character，可在寻路前Auto Switch至一个全部由可识别Character组成的队伍，寻路完成后再切回原队，确保Auto 寻路Stable执行

2. **历练点使用**：
   - Auto 检查是否可以领取历练点奖励（需使用120体力）
   - Auto 领取历练点奖励

3. **双倍Friendship度获取**：
   - **在好友的Serenitea Pot内，使用历练点完成Daily Commissions可获取双倍Friendship度**
   - **需保持队伍为4人队伍，但可通过Settings让指定位置Character离队，实际出战Character可≤2人**
   - Auto 进入好友的Serenitea Pot
   - Supports指定特定好友
   - Supports依次申请多个好友Serenitea Pot
   - 可让指定位置Character离队，确保实际出战Character符合需求

4. **Auto 检查是否可以使用历练点完成4个任务**：
   - 如果运行时未识别到 完成4个任务，不领取历练点奖励

5. **Auto Go toAdventurer协会领取奖励**：
   - 领取历练点奖励后，Auto Go to指定地区的Adventurer协会领取Daily Commissions奖励
   - Supports多个地区选择（Mondstadt、Liyue、Inazuma、Sumeru、Fontaine、Nod-Krai、Snezhnaya等）
   - Auto 进行对话交互，完成奖励领取

## 参数SettingsGuide / Instructions

### 基本Settings
| Guide / Instructions | 默认值 | 示例 |
|------|--------|------|
| 需要领取Friendship的队伍名称（不填则不Switch Party） | 无 | "Friendship队" |
| 移动专用队伍名称（可选） | 空 | "移动队" |
| > 用途：若Friendship队伍中包含 BGI 尚未Supports的新Character，导致Auto 寻路Defeat，可在此Settings一个全部由老Character组成的队伍。脚本会在寻路前Auto Switch至该队伍，寻路完成后再切回Friendship队伍领奖。留空则不启用此Features。 | | |
| 关闭Go toStatue of The SevenSwitch Party | 未勾选 | 勾选后不传送到Statue of The Seven |
| 直接使用历练点完成Daily Commissions<br>（全Character满Friendship时Recommended启用） | 已勾选 | 勾选后不获取双倍Friendship |
| Go to指定地区的Adventurer协会领取奖励 | "Mondstadt" | "Fontaine" |

### Serenitea Pot双倍FriendshipSettings
|Guide / Instructions | 示例 |
|------|------|
| (选填)指定好友名称 | "Traveler123","321者行旅" |
| (选填)申请好友数(≤7) | "5" |
|让1号位Character离队 | 勾选 |
| 让2号位Character离队 | 勾选 |
| 让3号位Character离队 | 勾选 |
| 让4号位Character离队 | 勾选 |

## 使用建议

### 双倍Friendship度获取流程
1. 先**自行**消耗120体力（获得历练点）
2. Auto 进入好友Serenitea Pot
3. 让指定位置Character离队（根据Settings）
4. 打开冒险之证领取历练点奖励
5. 返回大世界
6. 若Settings了移动专用队伍，脚本会先Switch至该队伍进行寻路，抵达Adventurer协会后再切回Friendship队伍
7. 领取Daily Commissions奖励

### Character离队策略
- 当需要获取双倍Friendship时，建议只保留2个需要提升Friendship的Character在队伍中
- 勾选需要离队的Character位置（1号位为最Left SideCharacter）
- **Note**：不能同时让所有Character离队（至少保留1个Character在队伍中）
- 离队操作在进入Serenitea Pot后Auto 执行

### 移动专用队伍使用策略
- **何时使用**：若您的Friendship队伍中包含 BGI 尚未Supports的新Character（如刚上线Character），Auto 寻路可能会因无法识别Character而Defeat。
- **如何Settings**：在游戏内创建一个全部由 BGI 已SupportsCharacter（如老Character）组成的队伍，例如“移动队”。将此队伍名称填入“移动专用队伍名称”Configuration项。
- **脚本行为**：在领取完历练点、返回大世界后，脚本会先Switch至该队伍执行寻路，成功到达Adventurer协会后再Switch回原来的Friendship队伍，然后进行对话领奖。
- **效果**：确保寻路过程Stable可靠，同时不影响后续的领奖队伍（Friendship队伍）。

### Adventurer协会地区选择
- RecommendedSettings为"Nod-Krai"，路程较短
- 可根据需要选择Other地区

## FAQ

**Q：为什么Nope进入好友Serenitea Pot？**  
A：请检查：
1. 是否已禁用双倍Friendship（**直接使用历练点完成Daily Commissions**被勾选）
2. 好友名称是否正确（区分大小写和空格）
3. 好友Serenitea Pot权限是否Settings为"允许直接加入"
4. 网络连接是否良好
5. 是否非Combat状态

**Q：CharacterNope离队怎么办？**  
A：请检查：
1. 是否正确勾选了Character位置
2. 游戏是否处于可Switch Party状态

**Q：为什么Switch PartyDefeat？**  
A：可能因为：
1. 处于联机模式
2. 队伍名称Settings错误
3. 无法正确识别游戏界面

**Q：Adventurer协会奖励Nope领取怎么办？**  
A：请检查：
1. 是否已经完成所有Daily Commissions
2. 是否已经领取过奖励
3. Auto 寻路是否正常执行
4. 队伍是否4人
5. BGI是否最新版
6. BGI是否未适配新Character → 若因新Character导致寻路Defeat，可Settings“移动专用队伍”来解决

**Q：寻路时提示无法识别Character或寻路Defeat？**  
A：这通常是因为当前队伍中包含 BGI 尚未Supports的新Character。请按以下步骤解决：
1. 在游戏中创建一个**仅由老Character（BGI 已Supports）组成的队伍**，并记住其名称。
2. 在脚本Settings中，将“移动专用队伍名称”填写为该队伍名称。
3. 脚本会在寻路前Auto Switch至此队，寻路完成后再切回原队，从而避开新Character的识别问题。

## Precautions / Notes

1. 游戏需运行在**1920×1080分辨率**下
2. 进入好友Serenitea Pot需要**网络连接良好**
3. 双倍Friendship度需要在好友Serenitea Pot内，自己Character不超过2个Character时，领取历练点奖励
4. 若使用指定好友Features，请确保**好友名称完全匹配**
5. 确保有足够的历练点可以领取（需完成所有Daily Commissions并消耗120体力）
6. Adventurer协会领奖Features依赖Auto 寻路，请确保游戏内队伍为4人队伍
7. 若使用移动专用队伍，Friendship队伍无需满员，寻路完成后会Switch回Friendship队伍，请确保移动专用队伍为4人以便领奖