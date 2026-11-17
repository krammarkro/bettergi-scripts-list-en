# Artifacts实时评分

在原神CharacterArtifacts页面实时显示Artifacts评分

> 脚本开箱即用

## 效果Showing Off

<img src="assets/images/readme/show.webp" style="width: 60%" alt=""/>

## 使用要求

- BetterGI Version不低于 `0.61.0`。
- 使用原神简体中文界面。
- Recommended使用 `1920×1080`、16:9 分辨率和默认界面缩放。

## Usage

1. 启动“Artifacts实时评分”脚本。
2. 如图，打开Character界面的Artifacts页。  

<img src="assets/images/readme/role.webp" style="width: 80%" alt=""/>

3. 等待片刻，评分遮罩会Auto 出现。
4. SwitchArtifacts后，脚本会重新确认部位和词条，更新结果。

结束使用时，使用 BetterGI 中的停止脚本Shortcut Keys即可。

## 两种评分模式

### Character定向评分

脚本会在进入详情前尝试识别并缓存当前Character，Supports以下标题形式：

- `水元素 / Sangonomiya Kokomi`
- `Artifacts / Sangonomiya Kokomi`

<img src="assets/images/readme/get-role.webp" style="width: 80%" alt=""/>

识别成功后，浮窗的大分数会显示为“Character名：分数”。该分数会按Character的有效词条、元素及特殊评分规则计算。

Traveler会区分风、岩、雷、草、水、火元素，排行榜中也会显示为“Traveler（元素）”。

### Normal评分

如果直接进入详情页，Nope识别到前置Character，浮窗会显示Normal评分。

Normal评分不是只计算双暴。脚本会分别计算Artifacts对所有Character的评分，并取其中前 50% 的平均值；攻击、生命、防御、精通、充能和双暴等有效词条都会参与计算。

## 浮窗内容

- 大数字：当前Character定向评分，或NopeCharacter缓存时的Normal评分。
- 档位：`D`、`C`、`B`、`A`、`S`、`SS`、`SSS`、`ACE`、`MAX`。
- 识别词条：实际传入评分模块的主词条和四条副词条。
- 适配Character：当前Artifacts评分最高的前 10 名Character。

无法可靠解析的行会显示为红色“未识别 / --”。发现识别错误时，建议等待或Switch到另一件Artifacts后再切回来。

> 词条命中次数纯依赖最终值推测，可能与实际情况不符，还请谅解

## 评分数据

评分权重和Character特殊规则来源于 [miao-plugin](https://github.com/yoimiya-kokomi/miao-plugin)。评分仅用于Fast筛选和参考，不代表唯一的配装Conclusive；实际价值仍会受到队伍、武器、命座和玩法影响。

## 开发者Guide / Instructions

评分规则模块 `utils/artis-score-standalone.js` 完全由以下命令生成，请勿直接编辑生成文件：

```bash
node tools/crawl-standalone.js
```

可使用 `--branch` 指定 miao-plugin 分支。这个爬虫只用于更新来自 miao-plugin 的Character评分规则、权重、基础属性和特殊规则。

单条得分拆分、有效/无效标色、词条数估算等基本Stable的Showing Off逻辑维护在 `utils/artis-score-utils.js`，不放进爬虫模板，避免更新Character规则时误覆盖。
