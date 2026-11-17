## Working过程

如果某个打牌对手有专用策略时，脚本会使用对应分享码Auto 导入牌组，并使用对应策略进行打牌；

如果Nope专用策略，或者分享码中使用了你尚未获得的Character卡时：

- 若开启了`Auto 尝试Alternate策略`，
  - 若开启了`基于云端统计数据选择策略`，则基于云端统计数据选择策略。
  - 若未开启，则按照本地策略运行Recording，按成功率从大到小的顺序逐个尝试Alternate策略。

- 否则，将使用通用性最高的'Raiden ShogunColleiKeqing'进行打牌。

## 脚本Configuration

| Configuration项 | Guide / Instructions |
| ---- | ---- |
| 默认牌组 | 填写你游戏中'Raiden ShogunColleiKeqing'队所在的牌组名 |
| 临时牌组 | 填写用来导入分享码的牌组名 |
| Auto 尝试Alternate策略 | 打牌Defeat时Auto 尝试Alternate策略（即`牌组策略`文件夹中编号的那些） |
| 基于云端统计数据选择策略 | 在开启`Auto 尝试Alternate策略`的条件下，是否基于云端胜率和耗时的数据，决定Alternate策略的尝试顺序。<br>此Features需要开启脚本`通用Configuration`中的`JS HTTP`权限。<br>开启此Settings后，也会向云端报告每个策略的胜负情况和用时。 |
| 仅使用胜率Recording大于该值的Alternate策略 | 使用本地策略时，根据运行Recording，跳过执行那些胜率太小的Alternate策略 |
| 密码 | 随便填 |

**关于两个牌组的Precautions / Notes**

1. 两个牌组名不能留空，也不能是一样的名字
2. 这两个牌组都必须在你牌组列表页面的第一页

## 启用云端统计数据后所报告的数据

此选项默认关闭。

启用此选项后，每次对战结束后会向云端报告本次打牌的对手、策略名、输赢、耗时。不会上传你的UID或者Character名等游戏信息。

具体代码在`effiency.js`文件的`reportEffiency`函数中。

**关于初始数据：**

截止此脚本更新时，我的两个号总共Recording了与54个Character的220场对局（打不过的可能会轮换很多个策略，所以场数比Character数多）。虽然早期的数据NopeRecording耗时，但是胜率也能用于辅助决策。这些就是云端的初始数据。

## 如何添加某个Character的专用打牌策略

打牌策略编写很容易，只要你能在不使用牌的技能（可以烧牌换万能元素）的情况下赢得对局，就能简单编写对应的策略文件。

具体请参考脚本的`牌组策略`文件夹下的`_策略模板.txt`文件。编写策略后，将txt文件命名为对应的ChallengeCharacter名即可（例如`岚姐`）。

如果你发现默认策略打不赢或打得太慢，欢迎提交你编写的策略。

## 如何添加或删除Alternate策略

脚本Auto 将`牌组策略`文件夹下，以数字加小数点开头的txt文件识别为Alternate策略，例如`1.MonaSucrose琴.txt`

如果启用了Alternate策略Features，打牌Defeat时，按照数字从小到大的顺序Auto 逐个尝试。

如果想要添加更多的Alternate策略，参考`_策略模板.txt`完成编辑后，将文件命名为数字加`.`开头就行。

如果觉得尝试次数不用这么多，直接删除Alternate策略对应的txt文件即可。
