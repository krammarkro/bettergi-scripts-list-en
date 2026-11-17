# Auto Purchase Items - Instructions

## 📝 FeaturesGuide / Instructions

这个脚本可以Auto 购买原神游戏中各个商品的商品，Supports三种刷新周期：
- **每天刷新商品**：每天凌晨4点刷新
- **3天刷新商品**：每3天刷新一次
- **每周刷新商品**：每周刷新，可指定购买日
- **Recording系统**：避免重复购买，只购买刷新后的商品
- **标签系统**：Supports按标签批量禁用商人，也Supports按商品名跳过特定商品
- **智能容量限制处理**：当某个商品因“Inventory内容量已达上限”而购买Defeat时，脚本会Auto Recording该商品，**本次运行后续所有商人**都不会再尝试购买该商品，避免反复无效操作。
- **商品预设**：通过脚本目录下的“预设工具.html”保存多套商品组合，在Settings的下拉栏中一键调用(详见[商品预设](#-商品预设))

## ⚡ FastStarting Up

### 1. 准备Working & Precautions / Notes
1. **游戏分辨率**：1920×1080 解析度
2. **游戏时间**：脚本会Auto 调整白天/晚上时间
3. **Inventory空间**：确保有足够空间购买商品
4. **Mora**：确保有足够的Mora
5. **Recording系统**：购买Recording保存在 `record/Account名/` 目录下
6. **多人模式**：脚本只能在单人模式下运行
7. **刷新时间**：基于游戏服务器时间（GMT+8），每天4点刷新
8. **地图追踪Configuration**：请关闭 BetterGI Settings中“地图追踪行走Configuration”的“Auto 拾取”Features，以免脚本在执行Path时因Auto 拾取而中断或偏离Route


### 2. 首次使用
1. 打开脚本Settings界面
2. 输入要购买的商品
3. Settings每周商品购买模式
4. Settings要禁用的商人或标签
5. 保存Settings
6. 在主界面运行脚本



## ⚙️ SettingsGuide / Instructions
1. **Account名**：填写Account名，用于区分不同Account的购买Recording(为空则读取uid作为自定义CDRecording标识)
2. **要购买的商品**：输入商品名称，用空格分隔（Support的商人与商品请查看下方表格）
   -  建议直接复制商品名称贴上输入栏
   -  输入标签后会购买具有该标签的商人的所有商品
   -  填写"Artifact EXP"会Auto 购买所有Artifact EXP商人的全部Artifact EXP商品（Adventurer、Traveling Doctor、Lucky Dog系列ArtifactsArtifact EXP）；也可单独填写如"Adventurer金杯"只购买该商品
   ```
   示例：盐 Pepper Crab 圣水 Matsutake Chenyu Adeptea Crab Roe 稀少商品
   ```
3. **商品预设**：下拉选择已保存的预设，本次运行按该预设的商品组合购买
   - 选项由脚本目录下的“预设工具.html”Auto 维护，详见[商品预设](#-商品预设)
   - 选择“不使用预设”（默认）则按上方“要购买的商品”栏购买
4. **每周商品购买方式**：
   - 0：跟随游戏系统周期Auto 判断
   - 1-7：指定周几购买（1=周一，7=周日）
   - **适用范围**：包含所有每周刷新的商品
     - 周一刷新商品
     - 周四刷新商品
   - **每月1号刷新商品**：不受此Settings影响，刷新即购买
5. **禁用标签或商品**：可以输入要禁用的标签或商品名（空格分隔），如：
   ```
   示例：黑心商人 Nod-Krai 卡琵莉亚 大碗茶
   ```
   禁用后，脚本会跳过这些商人或带有指定标签的商人，不会Go to购买。
   
   可以使用国家/地区（如"Mondstadt"、"Liyue"）或Other标签(如商人信息总览中的标签)
6. **是否跳过调整时间动画**：开启后会啟用时瞬跳过调整时间动画
7. **无视购买Recording强制购买**：开启后会忽略购买Recording，重新购买所有商品
8. **Debug模式**：禁用时以下两个子选项均不生效
   - **显示详细Log**：开启后显示详细执行Log
   - **指定NPC和商品**：格式如 `布兰琪 盐 Pepper，莎拉 Flour`，只运行指定NPC并只购买其指定商品（NPC和商品可多选，多组用逗号分隔；只填NPC名则购买该商人全部商品），用于测试指定Route与商品

### 购买Recording系统Guide / Instructions
脚本会Auto Recording购买时间，避免重复购买：
1. **每天刷新商品** - 每天凌晨4点刷新
2. **3天刷新商品** - 每3天刷新一次
3. **每周刷新商品** - 每周固定週一购买
   - 周一刷新商品：按Settings决定是否购买
   - 周四刷新商品（Artifact EXP商人）：同样受Settings控制
4. **每月1号刷新商品** - 每月1号凌晨4点刷新


购买Recording保存在：`record/你填的Account名/records.json`
- 下次执行时只购买已刷新商品
- 可通过"无视购买Recording强制购买"选项重置


## 📦 商品预设

通过脚本目录下的 **预设工具.html** 保存多套商品组合，避免每次更换商品组合都手动修改商品栏。

### 使用流程
1. 用 **Edge 或 Chrome** 浏览器打开脚本目录下的 `预设工具.html`
2. 点击“选择脚本文件夹”，选择 BetterGI 安装目录中的脚本文件夹（形如 `D:\Better GI\User\JsScript\Auto Purchase Items`）
3. 新建预设并填写商品组合，写法与脚本Settings里的商品栏一致，改动会Auto 保存到 `record/presets.json`
4. 在 BetterGI 脚本Settings的“商品预设”下拉栏选择要使用的预设并运行脚本，即按该组合购买；选择“不使用预设”则按“要购买的商品”栏购买

### Guide / Instructions
- 预设全局共享（不区分Account），保存在 `record/presets.json`，脚本更新时Auto 保留
- 预设的新建/重命名/删除/导入会**Auto 同步**到 BetterGI Settings中“商品预设”下拉栏；同步后需在 BGI 中**重新打开JS脚本Configuration页**才能看到同步后的选项
- 若下拉栏残留的预设已被删除（如删除全部预设后下拉栏显示为空），脚本运行时会提示并**Auto 回退为按“要购买的商品”栏购买**，同时把下拉栏复位为“不使用预设”
- “不使用预设”为下拉栏默认项与保留名，不能用作预设名
- 工具未连接文件夹时（或浏览器不Supports直连），改动暂存在浏览器中：可用“导出 presets.json”手动放入脚本 `record` 文件夹，或用“导入”恢复备份
- 若通过 BetterGI 脚本仓库更新脚本，`预设工具.html` 可能被覆盖为原版，即缓存在浏览器里的内容会丢失，如需保存需自行备份；`record/presets.json` 不受影响，重新打Time for Work!具会Auto 补回下拉选项


## 📋 商人与商品Supports表

### 如何查看Supports的商品？
- **查看本文件下方表格**：包含所有Supports的商人与商品

| 所在地 | 商人名 | 每天刷新商品 | 3天刷新商品 | 每周刷新商品 | 标签 |
|--------|--------|-------------|------------|-------------|------|
| Mondstadt-Windrise | 克罗丽丝 | - | Snapdragon、Mint、Wolfhook、Valberry、Philanemo Mushroom | - | 移动 |
| Mondstadt-Springvale | 神奇的霍普金斯 | 圣水 | - | - | 稀少商品 |
| Mondstadt-Springvale | 杜拉夫 | Raw Meat、Fowl、Bird Egg | - | - |  |
| Mondstadt-Mondstadt | 布兰琪 | 盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat | - | - | 杂货店 |
| Mondstadt-Mondstadt | 莎拉 | - | - | Flour、Cream、Smoked Fowl、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage |  |
| Mondstadt-Mondstadt | 芙萝拉 | - | Sweet Flower、Windwheel Aster、Cecilia、Small Lamp Grass、Calla Lily | - |  |
| Mondstadt-Mondstadt | 石榴 | - | - | Adventurer金杯、Adventurer尾羽、Adventurer头带、Adventurer之花、Adventurer怀表 | Artifact EXP商人 |
| Mondstadt-Mondstadt-天使的馈赠 | 查尔斯 | 冰Wolfhook汁、BerryMint饮、Apple酿、气泡酸莓汁 | - | - | 独立地图、稀少商品 |
| Mondstadt-Millhaven | 本瑟姆 | - | - | Flour、Cream、Smoked Fowl、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage |  |
| Mondstadt-Dornman Port | 菲乐丝 | - | - | Flour、Cream、Smoked Fowl、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage |  |
| Liyue-Liyue Harbor | 阿山婆 | Xiao Lantern | - | - |  |
| Liyue-Liyue Harbor | 石头 | Iron Chunk、White Iron Chunk、Noctilucous Jade | - | - |  |
| Liyue-Liyue Harbor | 东升 | 盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat、Rice、Shrimp Meat、Tofu、Almond | - | - | 杂货店 |
| Liyue-Liyue Harbor | 卯师傅 | Fish、Crab | Bamboo Shoot、Lotus Head、Matsutake、Mushroom、Carrot、Radish、Jueyun Chili | Flour、糖、Sausage、Ham |  |
| Liyue-Liyue Harbor | 老孙 | Fish、Crab、Shrimp Meat | - | - |  |
| Liyue-Liyue Harbor | 老高 | Fish | - | - |  |
| Liyue-Liyue Harbor | 长顺 | Potato | Cor Lapis、Electro Crystal | 糖、Cheese |  |
| Liyue-Liyue Harbor | 琳琅 | - | -  | Traveling Doctor的药壶、Traveling Doctor的枭羽、Traveling Doctor的方巾、Traveling Doctor的银莲、Traveling Doctor的怀钟 | Artifact EXP商人 |
| Liyue-Liyue Harbor | 张顺 | - | - | Lucky Dog之杯、Lucky Dog鹰羽、Lucky Dog银冠、Lucky Dog绿花、Lucky Dog沙漏 | Artifact EXP商人 |
| Liyue-Liyue Harbor | 博来 | - | Apple、Sunsettia、Fish、Starconch | - |  |
| Liyue-Liyue Harbor | 阿桂 | - | Qingxin、Violetgrass、Horsetail、Lotus Head、Mist Flower Corolla、Flaming Flower Stamen | - |  |
| Liyue-Qiongji Estuary | 朱Boss | 大碗茶 | - | - | 稀少商品 |
| Liyue-Wangshu Inn | 菲尔戈黛特 | - | Matsutake、Silk Flower、Violetgrass | Butter、Sausage |  |
| Liyue-Stone Gate | 老周叔 | 大碗茶 | - | - | 稀少商品 |
| Liyue-Qingce Village | 小白 | - | Tofu、Almond、Silk Flower | Glaze Lily(每月刷新) |  |
| Liyue-Qingce Village | 凯叔 | 大碗茶 | - | - | 稀少商品 |
| Liyue-Yilong Wharf | 丰泰 | Rice、Tofu | Clearwater Jade、Cor Lapis、Noctilucous Jade、Violetgrass、Silk Flower、Jueyun Chili、Chenyu Adeptea | Crab Roe |  |
| Liyue-Yilong Wharf | 连芳 | - | Chenyu Adeptea | - |  |
| Inazuma-Ritou | 小畑 | Crab、Fish、Shrimp Meat | Sea Ganoderma | - |  |
| Inazuma-Ritou | 秋月 | Iron Chunk、White Iron Chunk、Electro Crystal | - | - |  |
| Inazuma-Ritou | 山城健太 | Eel Meat | Sango Pearl | Lucky Dog之杯、Lucky Dog鹰羽、Lucky Dog绿花、Lucky Dog银冠、Lucky Dog沙漏 | Artifact EXP商人 |
| Inazuma-Ritou | 卡琵莉亚 | - | Dandelion Seed | - |  |
| Inazuma-Byakko Plain | 若紫 | - | - | 「四方八方之网」 |  |
| Inazuma-Inazuma City | 葵 | 盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat、Rice、Shrimp Meat、Tofu | Naku Weed | - | 杂货店 |
| Inazuma-Inazuma City | 志村勘兵卫 | Fish、Crab | Seagrass、Lavender Melon、Radish | Sausage、Bacon、Flour、糖 |  |
| Inazuma-Inazuma City | 智树 | 团子Milk | - | - | 稀少商品 |
| Inazuma-Inazuma City | 木南杏奈 | 特制风味Mushroom Pizza | - | - | 稀少商品 |
| Inazuma-Watatsumi Island | 清子 | - | - | Milk、Tomato、Potato、Wheat、Tofu |  |
| Sumeru-Gandharva Ville | 阿什帕齐 | Raw Meat、Fowl | Bird Egg、Rukkhashava Mushrooms | Spice |  |
| Sumeru-Sumeru City | 朱特 | - | Harra Fruit、Padisarah | Spice |  |
| Sumeru-Sumeru City | 阿夫辛 | - | - | Adventurer金杯、Adventurer尾羽、Adventurer头带、Adventurer之花、Adventurer怀表 | Artifact EXP商人 |
| Sumeru-Sumeru City | 珀姆 | Fish、Crab、Shrimp Meat | Seagrass | - |  |
| Sumeru-Sumeru City | 哈马维 | 盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat、Rice、Tofu、Shrimp Meat | Harra Fruit、Zaytun Peach | - | 杂货店 |
| Sumeru-Sumeru City-兰巴德酒馆 | 兰巴德 | Fish、Crab、Glabrous Beans | Starshroom | Flour、Sausage、Bacon、Spice、糖 | 独立地图 |
| Sumeru-Sumeru City-普斯帕咖啡馆 | 恩忒卡 | Coffee Beans | - | - | 独立地图 |
| Sumeru-Port Ormos | 拉玛 | 盐、Pepper | - | Spice、糖、Butter、Cheese |  |
| Sumeru-Port Ormos | 布特罗斯 | Fish、Crab、Shrimp Meat | - | - |  |
| Sumeru-Port Ormos | 秋蔚 | - | Crystal Chunk、Cor Lapis、Noctilucous Jade、Silk Flower | - |  |
| Sumeru-Port Ormos | 巴巴克 | - | Philanemo Mushroom、Dandelion Seed、Violetgrass、Qingxin、Naku Weed、Sango Pearl | - |  |
| Sumeru-Vanarana(梦境) | 兰玛尼 | - | Sunsettia、Harra Fruit、Zaytun Peach、Rukkhashava Mushrooms、Kalpalata Lotus | - | Vanarana(梦境) |
| Sumeru-Aaru Village | 阿扎莱 | Fish、Raw Meat、Glabrous Beans | Starshroom、Ajilenakh Nut、Zaytun Peach | Flour、Spice、糖 | 黑心商人 |
| Fontaine-Court of Fontaine | 布希柯 | 枫达、盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat、Glabrous Beans、Almond、Fermented Juice | Mushroom、Marcotte | - | 杂货店 |
| Fontaine-Court of Fontaine | 阿鲁埃 | 枫达、Coffee Beans | - | - |  |
| Fontaine-Court of Fontaine | 路易 | 枫达 | - | - |  |
| Fontaine-Court of Fontaine | 欧仁妮 | Tomato、Cabbage | Bulle Fruit、Marcotte、Sunsettia、Zaytun Peach、Ajilenakh Nut、Valberry、Rainbow Rose | - |  |
| Fontaine-Court of Fontaine-德波大饭店 | 桑格内蒂 | 枫达 | - | Flour、Cream、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage | 独立地图 |
| Fontaine-Court of Fontaine-灰河 | 克洛莎 | - | - | Lucky Dog之杯、Lucky Dog鹰羽、Lucky Dog银冠、Lucky Dog绿花、Lucky Dog沙漏 | Artifact EXP商人 |
| Fontaine-Poisson | 安特曼 | Fish、Crab、Shrimp Meat | Romaritime Flower、Tidalga、Subdetection Unit | - |  |
| Fontaine-The Rusty Rudder酒馆 | 皮托 | Milk | - | Bacon、Ham、Sausage、Cheese | 黑心商人 |
| Natlan-Stadium of the Sacred Flame | 钦特利 | Potato | 烛伞Mushroom、Grainfruit、Cacahuatl、Embercore Flower、Withering Purpberry、Saurian Claw Succulent | - |  |
| Natlan-Stadium of the Sacred Flame | 艾库瓦 | - | - | Lucky Dog之杯、Lucky Dog鹰羽、Lucky Dog银冠、Lucky Dog绿花、Lucky Dog沙漏 | Artifact EXP商人 |
| Natlan-Stadium of the Sacred Flame | 布纳马 | 盐、Pepper、Wheat、Onion、Milk、Tomato、Cabbage、Potato、Glabrous Beans | Mushroom | - | 杂货店 |
| Natlan-Stadium of the Sacred Flame | 夏安卡 | - | - | Flour、Cream、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage |  |
| Natlan-Tequemecan Valley | 伊蜜 | - | Iron Chunk、White Iron Chunk、Crystal Chunk、Condessence Crystal、Spinel Fruit | - |  |
| Natlan-Easybreeze Resort | 穆托莉娜 | - | Brilliant Chrysanthemum、Saurian Claw Succulent、Skysplit Gembloom、Sprayfeather Gill | - |  |
| Nod-Krai-Nasha Town | 采若 | 盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat、Rye | - | - | 杂货店 |
| Nod-Krai-Nasha Town | 丽切娅 | - | Sweet Flower、Nocturnal Blossom、Frostlamp Flower | - |  |
| Nod-Krai-Nasha Town | 卡嘉 | - | - | Flour、Cream、Smoked Fowl、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage |  |
| Nod-Krai-Nasha Town | 雷科 | - | - | Lucky Dog之杯、Lucky Dog鹰羽、Lucky Dog银冠、Lucky Dog绿花、Lucky Dog沙漏 | Artifact EXP商人 |
| Nod-Krai-Nasha Town-旗舰 | 德米安 | 「皮拉米达的夜莺」、边陲之地、野浆果之路 | - | - | 稀少商品、独立地图 |
| Nod-Krai-Piramida | 科菲策 | Milk、Coffee Beans | Glowing Hornshroom、Dracolite | - | 黑心商人 |
| Snezhnaya-Snezhnaya堡 | 格里戈里 | Honey、盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat | - | - | 杂货店 |
| Snezhnaya-Snezhnaya堡 | 齐良诺夫 | 格瓦斯、香料Honey饮、凛冬冰酿 | - | - | 稀少商品 |
| Snezhnaya-Snezhnaya堡 | 雅罗斯拉夫 | - | - | Lucky Dog之杯、Lucky Dog鹰羽、Lucky Dog银冠、Lucky Dog绿花、Lucky Dog沙漏 | Artifact EXP商人 |
| Snezhnaya-Snezhnaya堡-老庭院餐厅 | 布图琳娜 | - | - | Flour、Cream、Smoked Fowl、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage | 独立地图 |
| Snezhnaya-Dawn Station | 哲列兹诺夫 | Honey、盐、Pepper、Onion、Milk、Tomato、Cabbage、Potato、Wheat | - | - |  |
| Snezhnaya-新基捷城 | 莎别夏 | - | - | Flour、Cream、Smoked Fowl、Butter、Ham、糖、Crab Roe、Jam、Cheese、Bacon、Sausage、Smetana、Rye Flour |  |
| Snezhnaya-新基捷城 | 芙莱斯妲 | - | Red Beet、Glaciafruit、Snowball Flower、Rimecurrant、笼酸浆、妖精绿艾、析晶褶伞 | - |  |
| Snezhnaya-新基捷城 | 普拉泽娜 | Rye、Honey | - | - | 黑心商人 |

### **以下为有效标签**
- **国家**：Mondstadt、Liyue、Inazuma、Sumeru、Fontaine、Natlan、Nod-Krai、Snezhnaya
- **地区**：Windrise、Springvale、Mondstadt、Liyue Harbor、Ritou、Inazuma City、Watatsumi Island等
- **小地图**：天使的馈赠、兰巴德酒馆、德波大饭店、灰河、The Rusty Rudder酒馆、老庭院餐厅等
- **商人**：克罗丽丝、神奇的霍普金斯、杜拉夫等（所有商人名）
- **移动**：指商人会移动，有机会购买Defeat
- **稀少商品**：指稀少商品
- **独立地图**：指需要进入独立空间的特殊地图，这些地图部份Path无法使用地图追踪Features，使用简易脚本到商人位置、有机会购买Defeat
- **黑心商人**：指Nope折扣的商人，价格较贵的商人
- **Artifact EXP商人**：指每周四刷新商品的Artifact EXP商人
- **杂货店**：指每天刷新Ingredients的杂货店，每个国家有一个。

> **⚠️ Snezhnaya国商人特别提醒**  
> 部分商人附近偶尔会出现**Character彩蛋**导致购买Path被遮挡或交互Defeat。

### **欢迎补充商人与商品与标签**

## 🔧 添加新商品

### 1. 添加商品图片
1. 截图商品图标，尺寸建议 90×90 像素
2. 保存为 PNG 格式，放在 `assets/images/` 目录下
3. 文件名建议使用中文，如：`新商品.png`

### 2. 添加到商人
在 `assets/npcs.json` 中找到对应商人，添加到相应的商品列表中：

```json
"_1d_foods": ["新商品"]  // 每天刷新商品
"_3d_foods": ["新商品"]  // 3天刷新商品
"_7d_foods": ["新商品"]  // 每周刷新商品
```

### 3. 更新商人与商品Supports表
将新商品添加到本文件的商人与商品Supports表中，方便Other用户查看。

## 🆕 添加新商人

### 1. 录制Path
1. 使用Path录制工具录制Go to商人的Path
2. 保存为 JSON 文件，命名格式：`地区-位置-商人名.json`
3. 放在 `assets/path/` 目录下

### 2. 添加商人数据
在 `assets/npcs.json` 中添加：

```json
"new_npc": {
  "name": "新商人名",
  "enable": true,
  "page": 2,              // 商店总页数
  "time": "any",          // any/day/night
  "path": "assets/path/地区-位置-新商人名.json",
  "_1d_foods": ["商品1", "商品2"],    // 每天刷新
  "_3d_foods": ["商品3"],             // 3天刷新
  "_7d_foods": ["商品4"],              // 每周刷新
  "tags": ["地区", "黑心商人"]    // 商人标签
}
```

### 3. 参数Guide / Instructions
- `page`: 商店的总页数
- `time`: 商人出现时间
  - `any`: 全天出现
  - `day`: 
  - `night`:
- `path`: Path文件位置

### 4. 更新商人与商品Supports表
将新商人添加到本文件的商人与商品Supports表中。

## ❓ FAQ

### Q: 脚本不购买任何商品？
A: 检查：
1. 是否在Settings中填写了要购买的商品
2. 商品名称是否正确（参考上方表格）
3. 游戏分辨率是否为 1920×1080
4. Character是否在单人模式
5. 是否有购买Recording导致商品未刷新

### Q: 如何知道Supports哪些商品名称？
A: 查看：
1. 本文件中的"[商人与商品Supports表](#-商人与商品Supports表)"
2. 脚本目录下的"[商人与商品Supports表.md](./商人与商品Supports表.md)"
3. 运行脚本时的Log输出会显示"用户启用了以下商品"

### Q: 为什么跳过某些商人？
A: 可能原因：
1. 该商人Nope你要购买的商品
2. 商人在禁用列表中
3. 购买Recording显示商品还未到刷新时间

### Q: 如何重置购买Recording？
A: 有几种方法：
1. 启用"无视购买Recording强制购买"选项
2. 删除 `record/你的Account名/records.json` 文件
3. 等待商品自然刷新

### Q: 每天什么时候刷新？
A: 游戏内的刷新时间是**每天凌晨4点**。脚本会考虑这个时间点：
- 如果当前时间在4点前，视为前一天
- 购买Recording基于4点刷新时间计算

## 📅 Changelog 
<details>

### v3.7.2
  - **新增**
    - 新增了9项新物品素材
    - 新增了3条新Route:`Snezhnaya-新基捷城-莎别夏`、`Snezhnaya-新基捷城-芙莱斯妲`、`Snezhnaya-新基捷城-普拉泽娜`
  - **调整**  
    - 调整了部分Route的特征匹配方式

### v3.7.1
  - **优化**
    - 对部分因模板识别阈值不合适而容易识别错误的物品添加了独立的阈值
    - 调整商人`Liyue-Yilong Wharf-丰泰`Path
  - **修复**
    - 修复了部分情况下WheatException / Error不购买问题

### v3.7.0
  - **新增**
    - 新增商品预设Features：通过脚本目录下的“预设工具.html”保存多套商品组合，保存后Auto 同步为Settings中“商品预设”下拉栏的选项，运行时一键调用
  - **优化**
    - 调整商人`Sumeru-Sumeru City-兰巴德酒馆-兰巴德`Path
  - **修复**
    - 修复Debug模式下部分Log不受“显示详细Log”开关控制的问题

### v3.6.5
  - **优化**
    - `无视Recording强制购买`Features在运行一次后Auto 关闭
    - 在购买界面截图匹配Defeat时添加额外的重试机会，Defeat后该商品不写入Recording
    - 调整商人`Sumeru-Sumeru City-阿夫辛`Path
  - **修复**
    - 修复了`Liyue-Liyue Harbor-琳琅`Route在Nope做任务的情况下无法进入到正确对话选项的问题
    - 修复了部分Artifact EXP类商品购买Defeat的问题

### v3.6.4
  - **优化**
    - 调整商人`Snezhnaya-Dawn Station-哲列兹诺夫`Path
    - 调整商人`Liyue-Yilong Wharf-丰泰`Path

### v3.6.3
  - **新增**
    - 新增了 fakeLog 的Version号Auto 传入
  - **修复**
    - 修复了运行每月刷新点位时，如果运行日期为大月的最后一天（x月31日），会Exception / Error跳过一个月的问题

### v3.6.2
  - **新增**
    - 新增Debug模式下指定商人和商品购买
  - **优化**
    - 优化了Artifact EXP类商品填写繁琐问题，现在在商品栏填入“Artifact EXP”即可映射到所有Artifact EXP商品
    - 调整商人`Snezhnaya-Dawn Station-哲列兹诺夫`Path
  - **调整**
    - 调整商品图片识别阈值，从0.8改至0.84

### v3.6.1
  - **新增**
    - 商人交互选项识别，为了解决到达目标追踪点后除目标NPC外还存在Other对话对象导致交互错误的问题
  - **优化**
    - 商店对话选项智能化：`布纳马`、`杜拉夫`、`齐良诺夫` 等有特殊选项的NPC不再以固定 F 次数交互，而是循环识别对话内容，持续 F 交互直到出现目标选项
    - 未能进入对话时Auto 跳过该商人并继续下一个，不进行无效的购买尝试
    - 调整商人`Liyue-Liyue Harbor-老高`、`Snezhnaya-Snezhnaya堡-齐良诺夫`Path
    - 合并`Fish` 商品识别图片，`Liyue-Liyue Harbor-老高`商品列表同步更新，并对旧名做了兼容处理
    - 优化了uid识别逻辑，降低了复杂性
  - **修复**
    - 修复了一处 fakeLog 问题

### v3.6.0
  - **优化“带括号商品”无法识别的问题**  
    - 针对 `「四方八方之网」`、`「皮拉米达的夜莺」` 等名称带有书名号（「」）的商品，此前若用户在Configuration中未加括号，脚本会因匹配Defeat而报错或跳过购买。  
  本次更新后，**脚本会Auto 忽略商品名称中的「」括号**。无论您填写的是 `四方八方之网` 还是 `「四方八方之网」`，脚本均能准确识别并正常购买，不再受括号格式困扰。
  - **调整**  
    - 调整商品图片识别阈值，从0.85改至0.8

### v3.5.10
  - **优化**
    - 调整商人`Liyue-Liyue Harbor-阿山婆`Path

### v3.5.9
  - **优化**
    - 调整商人`Mondstadt-Mondstadt-天使的馈赠-查尔斯`Path
    - 调整商品`冰Wolfhook汁`图片
    
### v3.5.8
  - **新增**
    - 适配ABGI进度显示Log，脚本运行过程中输出更详细的进度信息，方便追踪执行状态。
  - **优化**
    - 修改「Snezhnaya-Snezhnaya堡-齐良诺夫」Route，避开Character彩蛋刷新位置，减少因NPC乱入导致的购买Defeat。

### v3.5.7
  - **新增**
    - 新增了4项Snezhnaya新物品素材
    - 新增了5条Snezhnaya新Route:`Snezhnaya-Snezhnaya堡-格里戈里`、`Snezhnaya-Snezhnaya堡-齐良诺夫`、`Snezhnaya-Snezhnaya堡-雅罗斯拉夫`、`Snezhnaya-Snezhnaya堡-老庭院餐厅-布图琳娜`、`Snezhnaya-Dawn Station-哲列兹诺夫`
  - **调整**
    - 修改了一项拼写问题:卯师父->卯师傅;并解决了可能因更名引发的bug问题

### v3.5.64
  - 调整商品图片识别阈值
  - 0.75改至0.85

### v3.5.63
  - **优化**
    - 调整商人`Liyue-Liyue Harbor-老孙`Path

### v3.5.62
  - **优化**
    - 调整商人`Nod-Krai-Nasha Town-旗舰-德米安`Path

### v3.5.601
  - **新增**：`disabledTags` 现Supports禁用商品。
    - 除了原有的按标签禁用商人外，现在也可以直接填写商品名来跳过特定商品的购买。
  - **修复**：修复了「每周购买日」Settings未生效的问题。

### v3.41.601
  - **优化**
    - 调整按 F 推进对话，等待界面响应时间
    
### v3.4.601
  - **优化**
    - 适配原神“月之八”VersionUI变化
    - 优化进入商店购买页面的方式，现在脚本会Auto 检测是否成功进入商品界面，若未进入则Auto 重试。
    - 进入商店时不再盲目按F固定次数，避免在对话过程中多次按F误触Other选项或意外购买非目标商品。

### v3.3.6
- **修复**：周四刷新商品（Artifact EXP商人）刷新时间计算错误
  - 之前周一至周三尝试购买周四商品时，刷新时间会被错误Recording到下周四
  - 现在正确Recording为本周四，购买成功后更新为下周四
- **修复**：购买Recording被覆盖的问题
  - 同类型商品的购买Recording现在改为合并去重，不再覆盖原有Recording

### v3.3.5
- **新增**：已售罄商品识别与Recording。
  - Auto 识别售罄商品，会当作正常购买，正常Recording CD。
  - 即使运行前手动购买过，脚本也能正确识别并跳过，避免重复尝试购买。
- **回退**：移除多选商品项目、回退至手动输入商品名称

### v3.3.4
- **新增**：Inventory容量上限智能处理机制。
  - 当购买某商品时出现"当前物品在Inventory内的容量已达上限"，脚本会Auto 将该商品加入黑名单。
  - 黑名单商品在**本次脚本运行的后续所有商人**中均会被跳过，不再尝试购买。
  - 该机制可避免因Inventory满而反复卡住，大幅提升执行效率。

</details>

## 🤝 贡献指南

欢迎提交新的商人和商品Configuration！

1. **提交新的商人**：包含Path文件和商人数据
2. **提交新的商品**：包含图片和商品数据
3. **更新文档**：记得更新本README中的商人信息表
4. **标签补充**：欢迎为现有商人添加合适的标签
5. **问题反馈**：提供详细的重现步骤和Log

---

> Note：本脚本仅供Learning与研究使用，请遵守游戏使用条款。

``
