# MiliastraExperienceAutomation

千星奇域每周刷取经验值

**Note：当前由于相应地图频繁下架，默认地图也未逃过此劫，因此请自行在运行前查找可刷取的地图，将房间号填到Settings中**

### 🌟 Feature Overview

- Auto 重复通关指定奇域关卡，Efficient刷取经验值。
- Auto 追踪每周经验获取进度，达到上限后再次执行将Auto 跳过，避免重复刷取。
- 执行完毕后Auto 返回Teyvat大陆，不干扰OtherAuto 化流程。

### 📖 Usage

- 将本脚本添加至您的Configuration组中。
- 右键点击脚本自定义Configuration项（当同时Configuration了多个关卡id时，假设Settings了20次循环，会以20次A，然后20次B这样的形式依次循环）。
- 点击运行按钮。

### 🛠️ 脚本Configuration

| Configuration项         | 描述                      | 默认值        |
| -------------- | ------------------------- |------------|
| goToTeyvat     | 完成后返回Teyvat大陆      | true       |
| room           | 奇域关卡关键词或关卡 GUID（支持多个id，用中文或英文逗号隔开） | 7070702264 |
| force          | 忽略本周经验值已达上限    | false      |
| thisAttempts   | 指定通关次数              | 0          |
| expWeeklyLimit | 每周可获取的经验值上限    | 4000       |
| expPerAttempt  | 每次通关获取的经验值数量  | 20         |

### ❗ Precautions / Notes

- 请确保游戏窗口分辨率比例为 `16:9`，否则可能影响脚本正常运行。
- 建议提前Settings好快捷键，便于在需要时Fast暂停或终止脚本。
