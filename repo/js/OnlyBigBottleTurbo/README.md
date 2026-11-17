# 只要大瓶Fast版

基于原Author **mno** 的 BetterGI 脚本《只要大瓶》制作的高速Version，用于Auto 选择并分解ArtifactsArtifact EXP，尽量将储存经验转换为大瓶。

- Author：**Purfeather**
- Version：`1.0.1`
- 适配：原神 `7.0`、BetterGI `0.64`
- 原脚本：[bettergi-scripts-list / 只要大瓶](https://github.com/babalae/bettergi-scripts-list/tree/main/repo/js/%E5%8F%AA%E8%A6%81%E5%A4%A7%E7%93%B6)

## 更新Recording

- `1.0.1`：采用更紧凑的默认点击延迟，少量提升点击速度。

## 脚本特点

- 按界面顺序Fast选择Artifacts，达到目标经验瓶后Auto 分解。
- SupportsSettings允许分解的最高星级。
- 五星Artifacts始终受到Protection，不会进入选择队列。
- Supports“只要大瓶”和“只要小瓶”两种模式。
- 可识别Inventory中的大小瓶数量，并按设定的临界值Auto Switch模式。
- Supports调整识别阈值和点击延迟，兼顾速度与Stable性。
- 识别结果存在冲突时会跳过对应Artifacts，避免误选。

## Usage

1. 在 BetterGI 中添加并运行“只要大瓶Fast版”。
2. 打开自定义Configuration，Settings允许分解的最高星级。
3. 选择目标经验瓶类型：
   - **只要大瓶**：尽量以大瓶为目标进行分解。
   - **只要小瓶**：以小瓶为目标进行分解。
4. 如需Auto Switch模式，填写“Auto Switch临界小瓶数量”：
   - 小瓶数量达到或超过设定值时，使用“只要大瓶”。
   - 小瓶数量低于设定值时，使用“只要小瓶”。
   - 留空则使用手动选择的目标经验瓶类型。
5. 首次运行时请Observing至少一轮完整过程，确认识图和点击均正常。

## 参数调整

默认识别阈值和点击延迟已经过实际测试，一般无需修改。

如果出现漏选，可适当降低Artifacts星级识别阈值；如果出现误识别，可适当调高。若点击偶尔未生效，优先增加“点击后Stable等待”时间。

调整参数后，建议先使用少量材料进行测试。

## 资源Guide / Instructions

`Assets/RecognitionObject` 保存脚本使用的界面按钮、Artifacts星级、经验瓶产物及Inventory数量识别图片；其中 `Inventory物品数字` 子目录保存数字 `0`～`9` 的数量识别模板。
