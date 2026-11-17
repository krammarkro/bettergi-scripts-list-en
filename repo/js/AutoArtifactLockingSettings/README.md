# 🔒 Auto ConfigurationArtifacts锁定方案

## ✨ 脚本简介

本脚本用于**Auto ConfigurationArtifacts锁定方案**。

锁定方案来源于 哔哩哔哩 @酸儒书生 的 [这期视频](https://www.bilibili.com/video/BV13YHQzMEAT)，脚本会Auto 识别游戏界面并完成所有Configuration操作，省去手动逐个Settings的繁琐过程。

## 🚀 Features特性

- 🎯 **Auto 识别套装** - 通过 OCR Auto 识别当前界面的Artifacts套装
- ⚙️ **批量Configuration方案** - Supports一次性Configuration多个套装的锁定方案
- 🔄 **覆盖已有方案** - 可选择是否覆盖已存在的锁定方案
- ⏱️ **延迟系数调节** - Supports自定义延迟系数，适配不同性能设备

## 📖 使用步骤

### 1️⃣ 前置要求

- 游戏分辨率Settings为 **16:9** (2560x1440 或 1920x1080)

- 游戏语言Settings为**简体中文**

- Artifacts「锁定辅助」页面的「通用锁定方案」勾选上1、3、4项，如图所示

  ![global-lock](assets/global-lock.jpg)

### 2️⃣ Configuration选项

在 「调度器」 中打开脚本Settings，Configuration以下选项：

| 选项 | Guide / Instructions |
|:---|:---|
| 覆盖已有方案 | 勾选后会删除已有方案并重新Configuration |
| 延迟系数 | 默认 1.2，运行Unstable时可调高至 1.4 或更高 |
| 需要Configuration的Artifacts套装 | 勾选需要Configuration的套装，Supports全选 |

### 3️⃣ 运行脚本

1. 在「调度器」中运行此脚本
2. 等待脚本Auto 完成所有Configuration

> 运行期间请勿操作鼠标键盘，脚本会Auto 控制游戏界面

## 🛠️ Supports的套装

脚本目前Supports 1.0~7.1（炉火，血红） 的Artifacts。

## 💬 问题反馈流程

1. 找到Log文件，Path为 BetterGI 安装目录的 `log` 目录下，Log文件名为 `better-genshin-impact年月日.log`
2. 屏幕Bottom-Left角的错误Log截个图
3. https://github.com/babalae/bettergi-scripts-list/issues 创建一个 issue，**上传截图和Log**，并 @bling-yshs

## Changelog

- 1.0.4 (2026-11-17)
  - 更新追加属性数量 1、2、3、4 条选项的点击坐标，适配新版界面布局

- 1.0.3 (2026-10-02)
  - 新增 `Heart of the Furnace` 与 `Scarlet Proof` 套装

- 1.0.2 (2026-07-10)
  - 新增 `Celestial Gift` 与 `Disenchantment in Deep Shadow` 套装，删除 `$any.plans[any].index` 参数

- 1.0.1 (2026-03-10)
  - 清理 `Artifacts锁定方案信息.json` 里的重复数据，脚本内容Nope实际修改

## 🙏 致谢

- 锁定方案来源：[@酸儒书生](https://space.bilibili.com/10411008)

## 👥 Author

- [bling-yshs](https://github.com/bling-yshs)
- [Bedrockx](https://github.com/Bedrockx)
- [qwecxzpoi](https://github.com/qwecxzpoi)
