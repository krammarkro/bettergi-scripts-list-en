# Auto 修改画质与音量

## 重要提醒

- 为了保证您的良好体验，请务必在Starting Up使用前阅读完本 README。
- 如果您在更新本 JS 后遇到问题，请在所有Configuration组中移除并重新添加本 JS，这是为了重建自定义Configuration文件以匹配新的Settings UI。
- 如果您发现运行此 JS 时失去焦点（也就是鼠标在操作别的窗口，而原神窗口在视觉上被覆盖），可以Go to BetterGI 主界面，点击Bottom-Left角Settings，找到通用FeaturesSettings，展开OtherSettings，找到失去焦点Auto 恢复，点击Right Side开关启用此Features。

## 作用Guide / Instructions

本 JS 可以根据用户的预设Auto 修改图像和声音Settings，避免了繁琐的手动调整流程。在您使用 BetterGI Auto 完成锄地等重复性任务前，可以运行本 JS，调低画质并静音以降低功耗；同样地，在锄地结束后也可以运行本 JS，调回高画质保证游戏体验。您还可以根据自己的需求开发新的用法。

## 兼容性

由于缺少修改画质的选项，本 JS **不Supports**云原神。

经过实测，本 JS Supports 1920 \* 1080、2560 \* 1440 分辨率。推测 3840 \* 2160 也可Supports。

本 JS 基于 OCR 识别，故**仅Supports**简体中文 UI。如果您平时使用的是其它语言，可以发 Issue Guide / Instructions。Roger That需求后，Author将酌情尝试通过在 JS 运行前后修改 UI 语言以解决此问题。

经过实测，本 JS 可以在大部分图像Settings下正常运行。但由于Author仅在高性能 PC 上测试了本 JS，其在老旧平台或移动设备上的运行效果是未知的。如果您遇到问题，请发 Issue Guide / Instructions您的运行平台和运行效果。

由于可能导致 BetterGI 崩溃，本 JS **不Supports**调整游戏分辨率。您可使用 [Unity 启动参数](https://docs.unity3d.com/cn/2021.1/Manual/CommandLineArguments.html)指定原神的窗口宽高等。

## Usage

在Configuration组中添加本 JS 后，右键本 JS，点击`修改JS脚本自定义Configuration`，即可在弹出的对话框中调整预设图像和声音Settings。

### 选项Guide / Instructions

预设Settings的标签名称与选项名称皆与游戏内名称一致，如果您发现不同，请发 Issue。

启用Fast模式后，选择选项将不再依赖 OCR，而是直接点击硬编码的坐标（也就是盲点），且点击更为迅速，在Nope默认选项的情况下耗时是Normal模式的一半左右。Fast模式可能在性能稍差的设备上不可用，因为 UI 动画速度可能过慢。如果您更追求Stable，不要勾选Fast模式。

每项Settings的第一个选项都是`默认`，在您选中它后本 JS 会**不修改**此选项。

Note，即使您预设`图像质量`选项不是`默认`或`自定义`，本 JS 依然会根据您的预设修改其余选项。所以如果您Settings了图像质量预设，又修改了其余选项为非预设的值，则在 JS 运行结束后`图像质量`将是`自定义`。

音量Settings只允许您设定不大于 10 的自然数，您可预设为 -1 以不修改对应的音量。Tips: 您还可直接在调度器中添加 Shell 指令以Auto 调整系统音量。

Thank You您耐心读完此 README，请勾选自定义Configuration中的复选框。
