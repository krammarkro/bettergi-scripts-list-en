# Teyvat杂事

## 一、介绍

本脚本适用于原神中一些特殊道具收集、个别Achievements、特殊操作等。

- Mondstadt清泉圣水【收集】
- Liyue铜雀上香【仪式】  
- Inazuma神樱抽签【仪式】【Achievements】
- Inazuma海螺宝箱【Achievements】【收集】
- Fontaine监狱领餐【Achievements】【收集】
- Natlan领取龙蛋【收集】
- 挪德Lucky!转盘【仪式】
- 挪德Today's Boon【收集】
- 挪德领取糖雕【仪式】【收集】
- Snezhnaya堡冰淇淋【仪式】【收集】

## 二、环境

在运行本脚本时，需要的游戏环境前提。

- 游戏Settings最好为默认。
- 游戏主线最好完成前期任务。
- 游戏中基本的Teleport Waypoint确保开启。
- 游戏分辨率Settings为`1920×1080`。
- 游戏中世界权限Settings为`不允许加入`。
- 行走位切勿Settings为Vesna

## 三、Precautions / Notes

相关Features有相关前置，请先确保自己是否做完。

<details>
<summary>Liyue铜雀上香</summary>

- 冒险等级40级
- 完成魈的传说任务『金翅鹏王之章·第一幕』
- 第二天接取并完成Liyue·世界任务『身后事·铜雀之迹』
- 第三天接取并完成Liyue·世界任务『身后事·All Is Well』
- 第四天接取并完成Liyue·世界任务『身后事·归于山中』

</details>

<details>
<summary>Inazuma神樱抽签</summary>

出现如下情况表示相关隐藏任务未做完，请检查并做完，避免后续任务卡掉

- 第一次神樱大社解签
- 解签对话中有『胧夜正中』
- Grand Narukami Shrine的玄冬小姐未到岗上班

Note：此处有多个隐藏任务，完成这系列任务需要现实世界4天，想完成该系列任务的，可搜索攻略，搜索关键字为【Grand Narukami Shrine解签任务】或【Dandelion Seed的归宿】

</details>

<details>
<summary>Inazuma海螺宝箱</summary>

- 用户自行将海螺屋附近的发光Investigating点Investigating了以及解密宝箱解开

</details>

<details>
<summary>Natlan领取龙蛋</summary>

- 平均模式：根据游戏中Inventory中各龙蛋的数量，或者脚本本地龙蛋Recording，做判断，进行平均领取龙蛋
- 随机模式：随机领取龙蛋
- 指定模式：指定选择钟爱的龙蛋

Note：运行该Features时，脚本会查看Recording文件是否为默认，龙蛋数目是否改动，以及两者数量是否一致，来判定是否打开Inventory进行龙蛋识别

</details>

<details>
<summary>挪德Today's Boon</summary>

- 接取并完成挪德莱卡·世界任务『餐食大事』

</details>

<details>
<summary>挪德领取糖雕</summary>

- 领取的糖雕默认是吃掉，防止卡Inventory
- 确保队伍Character未死亡
- 检查是否触发过秘闻馆提示，检查方法，携带密文馆Character进行对话
- Moon-Prayer Night的糖雕，必须过完挪德的主线剧情

Note：Character糖雕需要填写有该Character队伍名字

</details>

<details>
<summary>相关通知内容</summary>

- Inazuma抽签运势
- 监狱获得的食物名字&幸运签内容
- Inventory龙蛋数目
- 挪德转盘运势

</details>

## 四、食用方法

按照以下顺序进行SettingsConfiguration
- 运行BGI
- 点击【全Auto 】
- 点击【调度器】
- 【新增Configuration器组】
- 自己SettingsConfiguration组名称并确定
- 点击自己Settings的Configuration组名称
- 【添加】
- 选择【JS脚本】
- 勾选【AutoPickLitter】并确认
- 鼠标右键【Teyvat杂事（收集）】
- 选择【修改JS脚本自定义Configuration
- 自己看自身情况勾选



## 五、更新

### Version:2.2

优化内容如下：
- 整体代码进行全面重构
- 个别Route进行重新规划
- 添加糖雕添加Illuga、Linnea选项
- 添加Snezhnaya冰淇淋
- 重新排布README
Note：该为大Version更新，请重新Configuration