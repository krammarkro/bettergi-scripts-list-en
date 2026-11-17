# 采集小道具Switch

从Inventory小道具页Auto 查找并装备以下道具：

- `化种匣`：适合放在可采种植物Route之前。
- `王树瑞佑`：适合放在Auto Woodcutting脚本之前。
- `叁零式·便携营养袋`：适合放在需要体力补充的采集或Combat脚本之前。

脚本只负责装备Switch，植物采集Route与Woodcutting任务继续由对应脚本执行。当前装备已经符合Configuration时，脚本识别到“卸下”按钮后直接结束。

## Usage

1. 将脚本加入调度器Configuration组。
2. 右键打开“JS 脚本自定义Configuration”。
3. 选择 `化种匣`、`王树瑞佑` 或 `叁零式·便携营养袋`。
4. 将脚本放在对应采集任务之前。

示例编排：

```text
采集小道具Switch（化种匣）
植物采集Route
采集小道具Switch（王树瑞佑）
Auto Woodcutting-地图追踪版
采集小道具Switch（叁零式·便携营养袋）
需要体力的采集或Combat脚本
```

## 使用条件

- Account已经获得所选小道具。
- 从游戏主界面启动。
- 已在 BetterGI `0.64.0`、游戏 `1920×1080` 环境实机验证。

## 实机验证

- 化种匣能够识别“已装备”和“替换”状态；装备后，Sweet FlowerRoute连续识别到“Sweet Flower的种子”。
- 王树瑞佑能够从化种匣Switch成功；后续社区Woodcutting脚本识别到王树瑞佑，并完成一轮Birch WoodRoute，Recording获得Birch Wood 75。
- 叁零式·便携营养袋能够从化种匣Switch成功；装备后识别到"卸下"按钮。

## 资源Guide / Instructions

`assets/RecognitionObject` 中的三张 PNG 是Inventory小道具主体的实机识别模板。模板已避开快捷栏编号、状态角标、星级和数量区域。
