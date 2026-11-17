商店Artifact EXP周四凌晨4点刷新，可以自行选择想买的商人(默认全选)

根据体力代换计算，买完9个商人（共45个Artifacts）相当于用价值30体力的Mora换取了51体力的Artifact EXP。

所以真的不建议将Artifact EXP分解成Mora，如果你真的很缺。

**体力代换明细**（基准：1 体力 = 3,000 Mora ≈ 738 Artifacts经验）

- Mora基准：20 体力打地脉花 = 60,000 Mora（世界8+固定产出）
- 经验基准：20 体力打ArtifactsDomain ≈ 14,760 经验（统计期望值，含5星当Artifact EXP喂）

| 项目     | 计算                    | 折算体力  |
| -------- | ----------------------- | --------- |
| 花费Mora | 45 × 2000 = 90,000 Mora | 30 体力   |
| 获得Artifact EXP | 45 × 840 = 37,800 经验  | ≈ 51 体力 |

**运行Recording与多账户**

- 运行Recording保存在 `record/账户名/records.json`，每个商人点位独立Recording
- 买满5个或商品售罄后，该点位记为本周完成，周四凌晨4点刷新前再次运行会Auto 跳过；若运行途中中断，再次运行会从断点继续（已完成的点位跳过，没买完/Defeat的点位Auto 重试补买）
- 本周勾选的商人全部完成时，脚本会直接跳过运行

**账户名称Settings**

- 账户名用于区分多账户的运行Recording，默认为"默认账户"，Recording保存在 `record/你填的名称/records.json`
- 名称中的Path非法字符（\ / : * ? " < > |）会Auto 替换为下划线
- 留空则通过OCRAuto 识别当前游戏 UID 作为账户名，识别Defeat时使用"默认账户"文件夹

**取消运行限制**

勾选后无视Recording强制重跑所有勾选商人，仅本次生效，运行后会Auto 取消勾选，下次如使用此Features需要再次勾选。

## Changelog
### 2.6.5（2026.09.08）
1. 运行Recording保存形式修改为`.json`文件，Recording文件结构优化
1. Supports断点续跑Features，详情见`运行Recording与多账户`
1. 添加通过UID获取账户名称的Features，详情见`账户名称Settings`

### 2.6.4（2026.09.01）
1. 取消运行限制改为一次性勾选，运行后Auto 取消勾选
2. Recording完成时间增加售罄放行：购买数量为0时，仅当所有Route均售罄（本周已买过）才Recording，存在购买Defeat/Exception / Error的Route则不Recording（下次重试），避免手动购买售罄后运行，反复重跑
3. 优化Artifacts数量识别：OCR改用去掉末尾5字符取前面数字

### 2.6.3（2026.08.27）
1. 修复未打开Settings面板时商人默认值不加载导致 0 购买，及Defeat运行误记完成时间导致本周无法重试的问题
1. 修改了manifest, 使每次更新保持脚本名称不变，Version特性在描述中体现

### 2.6.2（2026.08.21）
1. 新增Snezhnaya点位

### 2.6.1（2026.08.14）
1. Route重命名
2. 修改Log输出内容
3. 固定Route运行顺序

### 2.6（2026.08.06）
1. 增加Inventory过期物品弹窗检测
2. 商人选择改为多选框
3. 增加OCR识别Artifacts购买数量
