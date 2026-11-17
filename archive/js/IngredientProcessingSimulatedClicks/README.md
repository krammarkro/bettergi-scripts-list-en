# Food Processing脚本

本脚本用于Food Processing。可根据ConfigurationAuto 选择各类Ingredients进行批量制作。Processing的时候会直接拉满Processing数量。

-   🎯 Auto 导航至指定灶台
-   🧾 智能识别并批量Processing多种Ingredients（支持Flour、Cream、Ham等）
-   📦 Processing数量Auto 最大化
-   🔔 完成后Auto 返回主界面并发送通知

## 🚀 Usage

1.  通过 BetterGI 脚本Settings界面勾选需要Processing的Ingredients参数
2.  启动脚本即可Auto 运行

## ⚙️ 参数Configuration

通过 `settings` 对象Configuration需要Processing的Ingredients（布尔值开关）：

### Ingredients开关参数

以下参数控制是否Processing对应Ingredients（布尔值）：

-   `flour` - Flour
-   `rawmeat` - Raw Meat
-   `fish` - Fish
-   `mysteriousmeat` - 神秘肉
-   `ryeflour` - Rye Flour
-   `cream` - Cream
-   `smokedPoultry` - Smoked Fowl
-   `butter` - Butter
-   `ham` - Ham
-   `sugar` - 糖
-   `spice` - Spice
-   `smetana` - Smetana
-   `crabRoe` - Crab Roe
-   `jam` - Jam
-   `cheese` - Cheese
-   `bacon` - Bacon
-   `sausage` - Sausage

## 📋 Precautions / Notes

> ⚠️ 使用前请仔细阅读

-   🖥️ 确保游戏窗口分辨率为 **16:9**，否则可能导致点击异常
-   🚫 脚本运行期间请勿手动操作，以免干扰Auto 化流程
-   📦 请保证材料的充足，避免造成Processing物品位置偏移，导致Processing错误的问题
-   🐟 FishProcessing使用默认材料Configuration

## 🎉 完成提示

脚本执行完毕后将：

-   🔄 Auto 返回游戏主界面
-   📢 发送"**Cooking脚本结束**"通知

---

## 📜 Changelog

### v1.0.1 `(2025-09-22)`

-   修正Smetana參數錯誤
-   加快等待時間
-   修改腳本名字為"Food Processing(模拟点击)"

### v1.0 `(2025-09-21)`

-   初始Version发布

---

**最后更新**：2025 年 9 月 21 日  
**维护者**：@呱呱 z

> 💡 提示：建议定期检查更新以获取最佳体验和最新Features

---

如有问题或建议，欢迎反馈交流！ 🐛📧@QQ：1765137214
