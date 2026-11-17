# Teyvat记事本

用于 BetterGI 的原神资源统计脚本。运行一次即可依次统计Wishes资源、Mora、Character经验书和Artifacts经验，并按账户保存Recording。

## 统计内容

- Wishes资源
  - Primogems
  - Intertwined Fate
  - Wishes资源总价值
  - 可用抽数
- Mora
- Character经验书
  - Wanderer's Advice数量
  - Adventurer's Experience数量
  - Hero's Wit数量
  - 经验书总经验
- Artifacts经验
  - 小经验瓶数量
  - 大经验瓶数量
  - Artifacts总经验

Artifacts总经验包含可分解的一至四星Artifacts、大小经验瓶和已储存经验。脚本仍会识别这些数据，但Recording文件只保留大小经验瓶数量与总经验。


## SettingsGuide / Instructions

| Settings | Guide / Instructions |
| --- | --- |
| Wishes资源 | 多选需要Recording的Wishes资源项目 |
| Mora | 勾选后识别并RecordingMora |
| Character经验书 | 多选三种经验书数量和总经验 |
| Artifacts经验 | 多选大小经验瓶数量和Artifacts总经验 |
| 发送统计通知 | 控制是否发送 BetterGI 通知 |
| 账户名称 | 用于区分不同账户的Recording文件，仅Supports 1～20 位中英文或数字 |

四个资源分类默认均不选择。某个分类至少勾选一项时，脚本才会执行该分类的识别；勾选的具体项目会写入本地Recording。

无效或空白的账户名称会Auto 使用 `默认账户`。

通知还需要在 BetterGI 的调度器通用Settings中启用“JS 通知权限”。

## 通知

为避免通知数量过多，全部项目开启时最多发送三条通知：

```text
Primogems-数量 | Intertwined Fate-数量 | 可用抽数-数量
```

```text
Mora-数量
```

```text
小经验瓶-数量 | 大经验瓶-数量 | Artifacts总经验-数量
```

## Recording文件

所有Recording保存在 `record` 文件夹中，每个账户使用一个文件：

```text
record/默认账户.txt
record/账户二.txt
```

所有勾选的本地Recording项目统一写入当前账户的同一个文件。同一账户再次运行时会追加新Recording，不会覆盖旧Recording。12 项可自由组合，也可以全部同时Recording。Mora使用原始整数Recording。每次运行只在该批Recording前写入一次时间：

```text
2026/07/29 15:12:30
Teyvat记事本-可用抽数-16
Teyvat记事本-Wishes资源总价值-2600
Teyvat记事本-Mora-750767
Teyvat记事本-Hero's Wit-24
Teyvat记事本-Adventurer's Experience-884
Teyvat记事本-Wanderer's Advice-1711
Teyvat记事本-经验书总经验-6611000
Teyvat记事本-小经验瓶-20
Teyvat记事本-大经验瓶-5
Teyvat记事本-Artifacts总经验-200000
```

关闭的统计项目不会写入对应Recording。

- BetterGI Version不低于 `0.55`
- 游戏分辨率以 `1920 × 1080` 为识别基准
- 游戏界面语言为简体中文
- 运行前确保Character处于可正常打开菜单的场景

OCR 或图片识别可能受到界面加载速度、分辨率和遮挡影响。如果某项统计Defeat，可返回主界面后重新运行。

## Changelog

1.0.3（2026/8/3）
经验书统计、Primogems和Intertwined Fate统计新增模板匹配，解决个位数ocr无法识别问题
识别3、5、8数字增加置信度判断
1.0.2（2026/7/30）
新增统计分类，可自定义选择Recording
1.0.1（2026/7/30）
新增经验书统计
优化Wishes资源统计
1.0.0（2026/7/29）
Teyvat记事本生日
