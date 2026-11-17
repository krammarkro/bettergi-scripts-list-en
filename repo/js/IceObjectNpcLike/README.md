# 冰造物 NPC LikeAuto 化

Author：一只低熵体  
Version：`1.3.0`<br>
全部Route预计总Like：`48`

脚本使用 BetterGI 地图追踪Go toSnezhnaya NPC 工位，Auto 完成两次冰造物放置、Like等待、删除和最终清理。脚本不读取游戏内存，不联网，也不使用第三方程序、KeyMouseScript、OCR 或Like图像识别。

## 使用条件

- BetterGI `0.64.0` 或更高Version；
- 简体中文游戏客户端；
- 16:9 游戏画面，至少 `1920×1080`；
- BetterGI 截图方式设为 `BitBlt`；
- 小地图保持“锁定方向”；
- 原神水平、垂直镜头灵敏度均保持默认值 `3`；
- 保持默认亮度并关闭 HDR、显卡滤镜等画面效果；
- 冰造物Shortcut Keys为 `T`，相关区域和Teleport Waypoint已解锁；
- 运行期间不要操作键盘和鼠标。

## 任务与Route解锁

- 完成三个聚所任务的共同第四幕“雪后曙光”后，Point 06、07、09、10 一带的 NPC 通常会显示；Point 08 的 NPC 显示还涉及现实时间第二天的“新雪来客”。参考：[《雪后曙光》教程](https://www.bilibili.com/video/BV172bX6XEPm/)、[《新雪来客》教程](https://www.bilibili.com/video/BV1nqbX6fEDS/)。
- NPC 未显示并不必然意味着无法获得Like：部分Account在未完成任务、NPC 不可见时，放置冰造物后仍实测获得Like。脚本不会识别任务进度或实际Like，请以自己的运行结果为准。
- 所有Route需要相关区域和NormalTeleport Waypoint已解锁。Point 12 会优先尝试“特殊招募计划”任务入口近路；若传送或落点核对Defeat，会Auto 改走从NormalTeleport WaypointLet's Go的完整Route，因此不要求解锁任务入口传送。

## Like机制

以下规则来自 [breadgrocery 大佬在 PR #3613 中分享的解包Configuration资料](https://github.com/babalae/bettergi-scripts-list/pull/3613)，并非脚本读取游戏数据所得：

- 冰造物在 NPC 出生点或活动中心约 `15` 米范围内时，可以触发Like判定；建筑、墙体遮挡或任务使 NPC 不显示，不一定影响Like。
- Configuration中存在可Like的 NPC，不代表现场一定能取得Like：有些场景或地块无法放置冰造物。Route表只列出本脚本已收录的工位，每位 NPC 按两次放置预计获得 `2` 赞。
- 脚本不会检测 NPC、判定半径或实际Like；若游戏Version或场景发生变化，请以实机结果为准。

## Usage

1. 在 BetterGI 中订阅或导入脚本。
2. 右键脚本，打开“修改 JS 自定义Configuration”。
3. 在“启用Route”多选框中选择需要执行的 Point；默认全选 Point 01～12，可按Account情况取消。
4. 将脚本加入调度器并运行。首次测试建议使用“Recommended顺序”。

新Configuration默认执行全部 12 个 Point，Route标签合计预计 `48` 赞；实际Like数量不做视觉识别。从旧版升级且保留了逐点开关Settings时，脚本会沿用旧选择，请在Configuration页检查“启用Route”。

## Route一览

| Route | 地点 | Like NPC | 预计Like | 备注 |
| --- | --- | --- | ---: | --- |
| Point 01 | 北国银行门口 | 伊兹麦洛夫、卡列林、尤洛娃 | 6 | 独立Route |
| Point 02 | 印记商店门口 | 叶芙琳娜、齐索斯琳娜、洛浦希娜、布柳什科 | 8 | 独立Route |
| Point 03 | 炉灰食堂门口 | 格里戈里、齐良诺夫 | 4 | 独立Route |
| Point 04 | 餐厅门口 | 叶里谢耶夫 | 2 | 独立Route |
| Point 05 | 铁匠附近 | 库兹米切夫 | 2 | 独立Route |
| Point 06 | Dawn Station玩具附近 | 切尔卡斯基、迈斯卡娅 | 4 | 路上经过热能恢复设施 |
| Point 07 | 车站餐厅 | 杜斯塔娅、伊格纳托夫 | 4 | 接续 08、09；路上经过热能恢复设施 |
| Point 08 | 车站火炬边 | 希什金娜、戈洛温、雅尔科娃 | 6 | 接续 Point 07 |
| Point 09 | 车站台子 | 蕾托娃 | 2 | 接续Route；08 关闭时使用Alternate Route |
| Point 10 | Dawn Station内 | 赫鲁塔廖夫、季米亚科夫、多洛霍夫 | 6 | 路上经过热能恢复设施 |
| Point 11 | 火炬书店 | 莫 | 2 | 路上经过热能恢复设施 |
| Point 12 | 冬契军训练场 | 雅洛维娅 | 2 | 优先任务入口近路；Defeat时改走NormalTeleport WaypointRoute |

### 车站连续Route

- Point 07、08、09 都开启时：`Point 07 → Point 08 → Point 09`；Point 09 关闭时在 Point 08 结束；
- Point 08 关闭、Point 09 开启时：Auto 改走 `Point 07 → Point 09` 完整Alternate Route；
- Point 07 关闭时：依赖当前位置的 Point 08、09 会Auto 跳过。

连续Route组不会被传送或热能恢复流程拆开。

## 运行模式

- **Recommended顺序**：默认模式，按 `01→02→03→06→05→04→07→08→09→10→11→12` 执行；关闭的Route会从顺序中跳过，07～09 仍作为连续组；
- **高Like优先**：执行全部已启用Route，并按Route组预计Like量排序；
- **高收益精简（6赞及以上）**：只执行预计Like达到 `6` 的Route组。

全部Route启用时，高收益精简模式会执行 Point 07～09 连续组（12 赞）、Point 02（8 赞）、Point 01（6 赞）和 Point 10（6 赞），合计预计 `32` 赞。

## 热能与镜头

脚本启动时会先返回固定Statue of The Seven恢复热能；进入Statue of The Seven范围后会Auto 恢复，所有目标环境均无需按 `F`。Point 01～12 **全部启用**时，三种运行模式都只在开局回Statue of The Seven一次；关闭任意Route后，脚本内部改为每完成 `4` 个 Point 返回Statue of The Seven。连续Route组不会拆开，若下一个组超过剩余额度，会在组Starting Up前提前恢复。热能策略由脚本Auto 选择，无需用户Settings。

按录制Route，Point 06、07、10、11 会在放置冰造物前经过热能恢复设施，预计每次恢复 `60` 点热能；每个 Point 的两次放置预计消耗 `10` 点。Recommended顺序把 Point 06 提前到第四个执行，以便更早经过恢复设施。脚本**不检测实际热能或沿途恢复是否触发**；全选时仅开局回Statue of The Seven的策略依赖这些恢复设施正常生效。

每个 Point 到位后，Route末尾的 `orientation` 负责确定水平视角；脚本再将垂直镜头推到上限，随后按自定义Configuration中的“冰造物放置镜头角度”向下移动，默认值为 `7500`。

检测到 `3840×2160` 或更高分辨率时，脚本默认在按 `T` 后额外等待 `800ms`。Other分辨率如果也出现界面动画未完成便点击的问题，可以手动启用相同时序补偿。

## 常用Settings

| Settings | 默认值 | 建议 |
| --- | ---: | --- |
| Route运行模式 | Recommended顺序 | 首次测试保持默认 |
| 启用Route（多选） | Point 01～12 全选 | 可按Account情况取消；Point 08、09 依赖 Point 07 |
| 冰造物放置镜头角度 | 7500 | 控制最终放置位置 |
| 强制启用 4K 时序补偿 | 关闭 | 非 4K 出现点击过早时开启；4K 会Auto 启用 |

## 故障排查与限制

- 多条Route同时出现Teleport Waypoint击偏移时，先完整退出并重启 BetterGI；
- 地图追踪反复摇摆时，确认 `BitBlt`、小地图锁定方向和Stable帧率，条件允许时可尝试 `2560×1440`；
- 脚本中途停止或报错后，请人工确认现场是否残留冰造物，并按 `T` 退出造物界面；
- Point 12 的近路会先单独传送并核对小地图位置；无法确认落点时会保守地走NormalTeleport WaypointRoute。Auto 回退尚需在未解锁任务入口的Account上实机验证；
- Log中的预计Like来自Route标签，脚本不会视觉识别实际Like、热能数值或删除结果。

## 致谢

Thank You [breadgrocery](https://github.com/breadgrocery) 大佬在 [PR #3613](https://github.com/babalae/bettergi-scripts-list/pull/3613) 中分享Like规则和完整 NPC 点位资料，让这份脚本补齐了Route与 NPC 对照表。Thanks~大佬！
