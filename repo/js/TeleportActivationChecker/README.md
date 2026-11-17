# Teleport Waypoint激活检测工具

用于系统检查地图中的Teleport Waypoint、Statue of The Seven、Domain和Other可Teleport Waypoint是否能够正常完成传送。

## 运行模式

- **继续上次检测**：从保存的断点继续；首次检测完成后Auto 复测Exception / Error点。
- **仅复测Exception / Error点**：只检测上次Defeat或超过慢速阈值的点。
- **重新检测全部**：清空本工具的检测状态和结果Log，从第一个点重新Starting Up。
- **查看检测报告**：不执行传送，直接Showing Off当前汇总和最后一次尝试仍Defeat的点位列表；用户取消任务不会被误记为未激活。

## 检测结果

- `local/results.log`：每次检测的逐条原始Recording。
- `local/checkpoint.json`：断点和点位状态，停止任务后用于继续。
- `local/report.json`：面向用户的最新汇总，包括通过、较慢、Defeat和待复核点。

脚本停止时会Auto 保存进度。传送Defeat不等于Teleport Waypoint一定未激活，Exception / Error点会进入复测列表，建议结合多次复测结果判断。

运行时默认显示鼠标穿透的状态遮罩，Showing Off当前进度、点位、耗时以及通过、较慢和Defeat数量；可在脚本Settings中关闭。

## 资源文件

- `assets/tp-points.json`：待检测Teleport Waypoint的地图、坐标、类型和区域信息。
- `assets/status-mask.html`：检测期间显示进度和统计结果的状态遮罩源码。
- `assets/report-mask.html`：Showing Off检测汇总和疑似未激活点位列表的报告遮罩源码。
