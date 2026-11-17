# 🎣 TeyvatAuto Fishing（全流程 + 自选）

一款基于 BGI 的全Auto Fishing脚本，Supports全Teyvat所有可追踪垂钓点。  
提供灵活筛选、Path控制、Auto 化Fishing与冷却Recording等完整Features，适用于日常收集、兑换材料获取与全图Fishing需求。

---

## ✨ Features概述

脚本可Auto 追踪并完成 BGI Supports的所有垂钓点，包括Path导航、时间调整、Fishing流程与冷却Recording等完整逻辑。
（更新鱼类数据后可能出现因版号落后导致无法运行的问题，在BGI本体的 `Settings` -> `帮助` ->`Version更新` ->`检查是否存在最新测试版` 更新到测试版即可正常使用）

---

## ⭐ 核心Features

- 🎯 **自由筛选**：按地区、鱼类、鱼饵自定义任务
- 🎁 **材料直钓**：Supports直接钓取兑换材料（如「The Catch」所需鱼类）
- 🌗 **Auto 调节时间**：根据目标鱼类Auto Switch昼夜
- 🧭 **特殊点位Supports**：可处理部分无法通过地图追踪到达的Fishing点
- 🔁 **从指定点继续任务**（需启用全部垂钓点）
- ⚔️ **CombatRoute可选**（默认关闭）
- ⏱ **Fishing超时自定义**
- ⏳ **定时Auto 停止（最多 24 小时）**
- 💎 **4 点Auto 领取月卡**（可选）
- 📒 **垂钓点冷却Recording**（多人模式Recording房主 CD）
- 🧲 **Auto 拾取**（可选）

---

## ⚠️ 使用Precautions / Notes

1. 部分点位包含Combat，队伍中请避免“双风”或“跑步Speed Up（非冲刺）”Character
2. PathingCharacter必须为**少男体型**
3. 鱼类 + 鱼饵的选择逻辑：
    - 所有选中的鱼类会加入任务列表
    - 若某鱼饵对应的鱼类未被选中，则该鱼饵对应的所有鱼类会被Auto 加入
4. 混合Route（Path追踪 + GCM）可能卡死，可在 JS Configuration中关闭键鼠Route
5. 请确保 **F2 未被占用**（用于多人模式检测）
6. Tsurumi Island点位SupportsAuto 使用「奇特的羽毛」

---

# 📘 ConfigurationGuide / Instructions

## 📂 基础Configuration

<details>
<summary><strong>筛选垂钓点</strong></summary>

### 钓取特定物品的兑换材料
字段：`path_sort_material`
- 选择后将忽略Other筛选
- 用于Fast钓取如「The Catch」「Ako's Sake Vessel」「Fleuve Cendre Ferryman」等材料

### 🗺 地区筛选
字段：`path_sort_area`
- 可多选
- 包含：Mondstadt、Liyue、Inazuma、Sumeru、Fontaine、Natlan、Snezhnaya、Nod-Krai、The Chasm: Underground Mines、Enkanomiya、Ancient Sacred Mountain

### 鱼类筛选
字段：`path_sort_fish`
- 可多选
- 若与鱼饵冲突，会Auto 补全任务列表

### 鱼饵筛选
字段：`path_sort_bait`
- 可多选
- 若鱼饵对应鱼类未被选中，会Auto 加入

### 禁用键鼠Route
字段：`block_gcm`
- 默认关闭
- 开启后禁用所有 GCM Route

### 启用CombatRoute
字段：`block_fight`
- 默认关闭

### 启用Tsurumi IslandRoute
字段：`block_tsurumi`
- 需拥有「奇特的羽毛」

### 奇特的羽毛使用方式
字段：`tsurumi_method`
- 方式 1：打开Inventory替换（默认）
- 方式 2：使用快捷更换
</details>

---

## ⚙️ 进阶Configuration

<details>
<summary><strong>垂钓点进阶Features & BGI 内置Fishing参数</strong></summary>

### 从指定垂钓点继续
字段：`path_continue`
- 仅在启用全部垂钓点时可用

### Auto 抛竿未上钩超时
字段：`time_out_throw`
- 默认：10 秒

### 整个任务超时时间
字段：`time_out_whole`
- 默认：300 秒

</details>

---

## 🧰 高级Configuration

<details>
<summary><strong>Happy特殊需求</strong></summary>

### 通知
字段：`启用通知`
- 每次进度更新时进行通知

### Auto 拾取
字段：`启用Auto 拾取`

### Auto 领取月卡（4 点）
字段：`启用4点领取月卡`

### 垂钓点 CD 统计
字段：`启用垂钓点CD统计`
- 默认开启
- 多人模式非房主Auto 禁用

### 自定义 CD Recording标识
字段：`自定义CDRecording标识`
- 留空则默认读取 UID
- 输入任意文本后将使用输入的文本作为自己世界的CDRecording标识

### 强制停止运行时间
字段：`小时` + `分钟`
- 两者同时选择才生效

</details>

---

## 🧪 开发者Configuration

<details>
<summary><strong>Debug模式</strong></summary>

### 指定Debug垂钓点
字段：`path_select`

### Debug时间
字段：`path_time`
- 全天 / 白天 / 夜晚

### DebugLog
字段：`developer_log`
- 目前不可用

</details>

---

# 📍 垂钓点详细信息

<details>
<summary>点击展开</summary>

| 地区 | 垂钓点名称 | 类型 | 鱼类 | 鱼饵 | CombatRoute | 键鼠(GCM) |
|------|------------|------|------|------|----------|----------|
| Fontaine | E001-Fontaine-垂钓点-Erinnyes ForestFoggy Forest PathSouthwest | Normal | Medaka、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Situation Controller、Maintenance Mek: Gold Leader | Fruit Paste Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E002-Fontaine-垂钓点-Erinnyes ForestLumidouce HarborNorthwest | Normal | Streaming Axe Marlin、Rippling Heartfeather Bass、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Gold Leader | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E003-Fontaine-垂钓点-Fontaine Research Institute of Kinetic Energy Engineering RegionCentral Laboratory Ruins南 | Normal | Medaka、Streaming Axe Marlin、Rippling Heartfeather Bass、Maintenance Mek: Initial Configuration、Maintenance Mek: Water Body Cleaner | Fruit Paste Bait、Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E004-Fontaine-垂钓点-Court of Fontaine RegionMarcotte StationSouthwest | Normal | Streaming Axe Marlin、Blazing Heartfeather Bass、Maintenance Mek: Initial Configuration、Maintenance Mek: Situation Controller | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E005-Fontaine-垂钓点-Court of Fontaine RegionCourt of FontaineNortheast | GCM | Streaming Axe Marlin、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Situation Controller | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  | 是 |
| Fontaine | E006-Fontaine-垂钓点-Court of Fontaine RegionCourt of Fontaine南 | Normal | Medaka、Streaming Axe Marlin、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Situation Controller | Fruit Paste Bait、Sugardew Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E007-Fontaine-垂钓点-Belleau RegionPoissonSouthwest | Normal | Medaka、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Platinum Collection | Fruit Paste Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E008-Fontaine-垂钓点-翡黎区芒索斯山东麓东 | Normal | Streaming Axe Marlin、Blazing Heartfeather Bass、Maintenance Mek: Initial Configuration、Maintenance Mek: Situation Controller | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E009-Fontaine-垂钓点-Beryl RegionElynas东 | Normal | Streaming Axe Marlin、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Initial Configuration | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E010-Fontaine-垂钓点-Beryl RegionElynasNortheast | Normal | Sandstorm Angler、Rippling Heartfeather Bass、Maintenance Mek: Initial Configuration、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Situation Controller | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E011-Fontaine-垂钓点-Beryl RegionRomaritime Harbor北 | Normal | Streaming Axe Marlin、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Situation Controller | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E012-Fontaine-垂钓点-Morte RegionFort Charybdis Ruins南 | Normal | Medaka、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Situation Controller、Maintenance Mek: Gold Leader | Fruit Paste Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E013-Fontaine-垂钓点-Morte RegionOpera Epiclese南 | Normal | Streaming Axe Marlin、Blazing Heartfeather Bass、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Situation Controller、Maintenance Mek: Gold Leader | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E014-Fontaine-垂钓点-诺思托伊区Petrichor南 | Normal | Streaming Axe Marlin、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Initial Configuration、Maintenance Mek: Water Body Cleaner、Maintenance Mek: Situation Controller、Maintenance Mek: Gold Leader | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  |  |
| Fontaine | E015-Fontaine-垂钓点-Court of Fontaine RegionOpera Epiclese西 | GCM | Streaming Axe Marlin、Rippling Heartfeather Bass、Blazing Heartfeather Bass、Maintenance Mek: Initial Configuration | Sugardew Bait、Sour Bait、Flashing Maintenance Mek Bait |  | 是 |
| Liyue | B001-Liyue-垂钓点-Cloud SeaLiyue HarborSoutheast | Normal | Sweet-Flower Medaka、Dawncatcher、Crystalfish、Betta、Pufferfish | Fruit Paste Bait、Redrot Bait、Fake Fly Bait |  |  |
| Liyue | B002-Liyue-垂钓点-Chenyu Vale: Upper Vale古树茶坡 | Normal | Medaka、Betta、Brown Shirakodai、Rusty Koi、Golden Koi、Jade Heartfeather Bass | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait、Sour Bait |  |  |
| Liyue | B003-Liyue-垂钓点-Chenyu Vale: Upper Vale古树茶坡东 | Normal | Medaka、Dawncatcher、Crystalfish、Betta、Rusty Koi、Jade Heartfeather Bass | Fruit Paste Bait、Redrot Bait、Fake Fly Bait、Sour Bait |  |  |
| Liyue | B004-Liyue-垂钓点-Chenyu Vale: Southern MountainMt. XuanlianSouthwest | Normal | Sweet-Flower Medaka、Dawncatcher、Akai Maou、Golden Koi、Jade Heartfeather Bass | Fruit Paste Bait、Redrot Bait、Fake Fly Bait、Sour Bait |  |  |
| Liyue | B005-Liyue-垂钓点-MinlinTianqiu Valley | Combat | Medaka、Crystalfish、Betta | Fruit Paste Bait、Redrot Bait | 是 |  |
| Liyue | B006-Liyue-垂钓点-MinlinMt. Aocang | Normal | Medaka、Sweet-Flower Medaka、Dawncatcher、Crystalfish、Abiding Angelfish | Fruit Paste Bait、False Worm Bait |  |  |
| Liyue | B007-Liyue-垂钓点-MinlinMt. Hulao东 | Normal | Medaka、Sweet-Flower Medaka、Dawncatcher、Crystalfish、Betta、Brown Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait |  |  |
| Liyue | B008-Liyue-垂钓点-Qiongji EstuaryGuili PlainsNortheast | Normal | Sweet-Flower Medaka、Betta、Akai Maou、Golden Koi、錆假龙、Brown Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| Liyue | B009-Liyue-垂钓点-Qiongji EstuaryLuhua Pool | Normal | Sweet-Flower Medaka、Betta、Akai Maou、Golden Koi、錆假龙、Brown Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| Liyue | B010-Liyue-垂钓点-Bishui PlainMt. Aocang东 | Combat | Medaka、Dawncatcher、Crystalfish、Brown Shirakodai | Fruit Paste Bait、False Worm Bait | 是 |  |
| Liyue | B011-Liyue-垂钓点-Bishui PlainWuwang Hill南 | Combat | Medaka、Sweet-Flower Medaka、Dawncatcher、Brown Shirakodai | Fruit Paste Bait、False Worm Bait | 是 |  |
| Liyue | B012-Liyue-垂钓点-Bishui PlainWangshu Inn西 | Normal | Sweet-Flower Medaka、Betta、Akai Maou、Golden Koi、Rusty Koi、Brown Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| Liyue | B013-Liyue-垂钓点-Bishui PlainYaodie Valley东 | Normal | Medaka、Betta、Brown Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait |  |  |
| Liyue | B014-Liyue-垂钓点-Bishui PlainQingce VillageNortheast | Normal | Sweet-Flower Medaka、Dawncatcher、Crystalfish、Betta、Brown Shirakodai、Bitter Pufferfish | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| The Chasm: Underground Mines | ZB001-The Chasm: Underground Mines-垂钓点-Underground Waterway西 | Normal | 花锵、Betta、Akai Maou、Brown Shirakodai、Bitter Pufferfish | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| The Chasm: Underground Mines | ZB002-The Chasm: Underground Mines-垂钓点-Nameless Ruins西 | Combat | Sweet Flower锵、Dawncatcher、Crystalfish、Akai Maou、Pufferfish | Fruit Paste Bait、Redrot Bait、Fake Fly Bait | 是 |  |
| Inazuma | C001-Inazuma-垂钓点-Yashiori IslandNazuchi Beach北 | Combat | Medaka、Lunged Stickleback、Purple Shirakodai、Bitter Pufferfish | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait | 是 |  |
| Inazuma | C002-Inazuma-垂钓点-Watatsumi IslandSuigetsu Pool东 | Combat | Medaka、Glaze Medaka、Dawncatcher、Crystalfish、Lunged Stickleback、Purple Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait | 是 |  |
| Inazuma | C003-Inazuma-垂钓点-Watatsumi IslandSangonomiya Shrine北 | Normal | Medaka、Glaze Medaka、Dawncatcher、Crystalfish、Lunged Stickleback、Purple Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait |  |  |
| Inazuma | C004-Inazuma-垂钓点-Seirai IslandAmakumo Peak北 | Normal | Medaka、Dawncatcher、Crystalfish、Purple Shirakodai、Pufferfish | Fruit Paste Bait、False Worm Bait、Fake Fly Bait |  |  |
| Inazuma | C005-Inazuma-垂钓点-Seirai IslandKoseki VillageSoutheast | Normal | Glaze Medaka、Lunged Stickleback、Akai Maou、Golden Koi、Rusty Koi、Purple Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| Inazuma | C006-Inazuma-垂钓点-Kannazuka甘金岛南 | Normal | Glaze Medaka、Lunged Stickleback、Purple Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait |  |  |
| Inazuma | C007-Inazuma-垂钓点-Narukami IslandRitou西 | Normal | Glaze Medaka、Lunged Stickleback、Akai Maou、Pufferfish、Bitter Pufferfish | Fruit Paste Bait、Redrot Bait、Fake Fly Bait |  |  |
| Inazuma | C008-Inazuma-垂钓点-Tsurumi IslandChirai Shrine西 | Normal | Medaka、Glaze Medaka、Dawncatcher、Crystalfish | Fruit Paste Bait |  |  |
| Inazuma | C009-Inazuma-垂钓点-Tsurumi IslandAutake PlainsSouthwest | Normal | Medaka、Lunged Stickleback、Akai Maou、Purple Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait |  |  |
| Inazuma | C010-Inazuma-垂钓点-KannazukaKujou EncampmentSoutheast | GCM | Raimei Angelfish | False Worm Bait |  | 是 |
| Enkanomiya | ZC001-Enkanomiya-垂钓点-The Serpent's Bowels南 | Normal | Crystalfish、Lunged Stickleback、Formalo Ray、Divda Ray | Fruit Paste Bait、Redrot Bait、Fake Fly Bait |  |  |
| Enkanomiya | ZC002-Enkanomiya-垂钓点-The Serpent's Heart北 | Combat | Dawncatcher、Akai Maou、Formalo Ray、Divda Ray | Fruit Paste Bait、Redrot Bait、Fake Fly Bait | 是 |  |
| Enkanomiya | ZC003-Enkanomiya-垂钓点-The Serpent's HeartNorthwest | Normal | Dawncatcher、流纹京紫鲽鱼、Formalo Ray、Divda Ray | Fruit Paste Bait、False Worm Bait、Fake Fly Bait |  |  |
| Natlan | F001-Natlan-垂钓点-境壁山Tecoloapan Bay东 | Normal | Pseudoshark Unihornfish、Medaka、Floral Rapidfighting Fish、Diving Rapidfighting Fish、Dusk Sunfish、Greenwave Sunfish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Natlan | F002-Natlan-垂钓点-Ochkanatlan东 | Normal | Medaka、Greenwave Sunfish、Dusk Sunfish、Pseudoshark Unihornfish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Natlan | F003-Natlan-垂钓点-OchkanatlanNortheast | Combat | Greenwave Sunfish、Floral Rapidfighting Fish、Pseudoshark Unihornfish | Spinelgrain Bait | 是 |  |
| Natlan | F004-Natlan-垂钓点-Ochkanatlan北 | Normal | Medaka、Dusk Sunfish、Pseudoshark Unihornfish、Diving Rapidfighting Fish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Natlan | F005-Natlan-垂钓点-Ochkanatlan南 | Normal | Medaka、Floral Rapidfighting Fish、Diving Rapidfighting Fish、Greenwave Sunfish、Dusk Sunfish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Natlan | F006-Natlan-垂钓点-Ochkanatlan西 | Normal | Diving Rapidfighting Fish、Floral Rapidfighting Fish、Pseudoshark Unihornfish | Spinelgrain Bait |  |  |
| Natlan | F007-Natlan-垂钓点-OchkanatlanNorthwest | Normal | Phony Phlogiston Unihornfish、Magma Rapidfighting Fish | Emberglow Bait |  |  |
| Natlan | F008-Natlan-垂钓点-Toyac SpringsToyac Springs | Normal | Magma Rapidfighting Fish、Phony Phlogiston Unihornfish | Emberglow Bait |  |  |
| Natlan | F009-Natlan-垂钓点-Tilted Branch CliffFlower-Feather Clan北 | Normal | Dusk Sunfish、Diving Rapidfighting Fish、Pseudoshark Unihornfish | Spinelgrain Bait |  |  |
| Natlan | F010-Natlan-垂钓点-Tilted Branch CliffFlower-Feather Clan西 | Normal | Medaka、Floral Rapidfighting Fish、Diving Rapidfighting Fish、Dusk Sunfish、Pseudoshark Unihornfish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Natlan | F011-Natlan-垂钓点-距石山Ancestral Temple东 | Normal | Magma Rapidfighting Fish、Phony Phlogiston Unihornfish | Emberglow Bait |  |  |
| Natlan | F012-Natlan-垂钓点-Atocpan西 | Normal | Phony Phlogiston Unihornfish、Secret Source Scout Sweeper | Emberglow Bait |  |  |
| Natlan | F013-Natlan-垂钓点-AtocpanNorthwest | Normal | Magma Rapidfighting Fish、Phony Phlogiston Unihornfish、Secret Source Scout Sweeper | Emberglow Bait |  |  |
| Natlan | F014-Natlan-垂钓点-Atocpan东 | Normal | Medaka、Floral Rapidfighting Fish、Greenwave Sunfish、Dusk Sunfish、Pseudoshark Unihornfish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Natlan | F015-Natlan-垂钓点-Easybreeze ResortColorfall Cliffs北 | Normal | Medaka、Floral Rapidfighting Fish、Greenwave Sunfish、Pseudoshark Unihornfish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Natlan | F016-Natlan-垂钓点-Easybreeze Resort呼呼丘Southwest | Normal | Floral Rapidfighting Fish、Diving Rapidfighting Fish、Dusk Sunfish、Pseudoshark Unihornfish | Spinelgrain Bait |  |  |
| Natlan | F017-Natlan-垂钓点-Easybreeze ResortEasybreeze MarketSouthwest | Normal | Medaka、Diving Rapidfighting Fish、Greenwave Sunfish、Dusk Sunfish | Fruit Paste Bait、Spinelgrain Bait |  |  |
| Ancient Sacred Mountain | ZF001-Ancient Sacred Mountain-垂钓点-Sea of Shifting Sentience | Normal | Magma Rapidfighting Fish、Secret Source Scout Sweeper | Emberglow Bait |  |  |
| Mondstadt | A001-Mondstadt-垂钓点-DragonspineSkyfrost Nail西 | Normal | Medaka、Venomspine Fish、Snowstrider、Tea-Colored Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait |  |  |
| Mondstadt | A002-Mondstadt-垂钓点-Starfell ValleyWhispering Woods南 | Normal | Aizen Medaka、Crystalfish、Venomspine Fish、Rusty Koi、Tea-Colored Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| Mondstadt | A003-Mondstadt-垂钓点-Starfell ValleyStormbearer Mountains | Normal | Medaka、Aizen Medaka、Dawncatcher、Crystalfish、Venomspine Fish、Golden Koi、Tea-Colored Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| Mondstadt | A004-Mondstadt-垂钓点-Brightcrown MountainsStormterror's Lair北 | Combat | Medaka、Aizen Medaka、Dawncatcher、Crystalfish | Fruit Paste Bait | 是 |  |
| Mondstadt | A005-Mondstadt-垂钓点-Brightcrown MountainsStormterror's Lair南 | Normal | Medaka、Aizen Medaka、Dawncatcher、Tea-Colored Shirakodai | Fruit Paste Bait、False Worm Bait |  |  |
| Mondstadt | A006-Mondstadt-垂钓点-Windwail HighlandDawn WinerySouthwest | Combat | Aizen Medaka、Dawncatcher、Venomspine Fish、Akai Maou、Tea-Colored Shirakodai、Pufferfish、Bitter Pufferfish | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait | 是 |  |
| Mondstadt | A007-Mondstadt-垂钓点-Windwail HighlandSpringvale北 | Normal | Medaka、Aizen Medaka、Venomspine Fish、Akai Maou、Tea-Colored Shirakodai、Pufferfish、Bitter Pufferfish | Fruit Paste Bait、Redrot Bait、False Worm Bait、Fake Fly Bait |  |  |
| Mondstadt | A008-Mondstadt-垂钓点-Windwail HighlandWindrise南 | Normal | Medaka、Aizen Medaka、Venomspine Fish、Tea-Colored Shirakodai | Fruit Paste Bait、Redrot Bait、False Worm Bait |  |  |
| Mondstadt | A009-Mondstadt-垂钓点-Windrest PeakMillhaven东 | Normal | Venomspine Fish、Akai Maou、Golden Koi、Cerulean Doppeldrake | Redrot Bait、Fake Fly Bait |  |  |
| Mondstadt | A010-Mondstadt-垂钓点-Windrest PeakDornman PortSouthwest | Normal | Aizen Medaka、Dawncatcher、Crystalfish、Cerulean Doppeldrake | Fruit Paste Bait、Fake Fly Bait |  |  |
| Mondstadt | A011-Mondstadt-垂钓点-Windrest PeakDornman Port南 | Normal | Dawncatcher、Tea-Colored Shirakodai、Pufferfish、Bitter Pufferfish、Cerulean Doppeldrake | Fruit Paste Bait、False Worm Bait、Fake Fly Bait |  |  |
| Sumeru | D001-Sumeru-垂钓点-Land of Lower SetekhDar al-ShifaSouthwest | Normal | Medaka、Dawncatcher、Akai Maou、True Fruit Angler、Lazurite Axe Marlin | Fruit Paste Bait、Redrot Bait、Sugardew Bait |  |  |
| Sumeru | D002-Sumeru-垂钓点-Land of Lower SetekhAaru Village | Normal | Medaka、Crystalfish、Sandstorm Angler、Sunset Cloud Angler、Halcyon Jade Axe Marlin | Fruit Paste Bait、Sugardew Bait |  |  |
| Sumeru | D003-Sumeru-垂钓点-Desert of Hadramaveth「Debris of Panjvahe | Combat | True Fruit Angler、Sandstorm Angler、Sunset Cloud Angler、Lazurite Axe Marlin、Halcyon Jade Axe Marlin | Sugardew Bait | 是 |  |
| Sumeru | D004-Sumeru-垂钓点-Lokapala JungleMawtiyima Forest | Normal | Peach of the Deep Waves、Sunset Cloud Angler、Lazurite Axe Marlin、Halcyon Jade Axe Marlin | Sugardew Bait |  |  |
| Sumeru | D005-Sumeru-垂钓点-VanaranaFane of Ashvattha北 | Normal | Medaka、True Fruit Angler、Sandstorm Angler、Sunset Cloud Angler、Lazurite Axe Marlin、Halcyon Jade Axe Marlin | Fruit Paste Bait、Sugardew Bait |  |  |
| Sumeru | D006-Sumeru-垂钓点-荒石苍漠Mount Temur南 | Normal | Dawncatcher、True Fruit Angler、Sandstorm Angler、Sunset Cloud Angler、Lazurite Axe Marlin、Halcyon Jade Axe Marlin | Fruit Paste Bait、Sugardew Bait |  |  |
| Sumeru | D007-Sumeru-垂钓点-Avidya ForestYazadaha Pool | Normal | Akai Maou、True Fruit Angler、Sandstorm Angler、Sunset Cloud Angler、Lazurite Axe Marlin、Halcyon Jade Axe Marlin | Redrot Bait、Sugardew Bait |  |  |
| Sumeru | D008-Sumeru-垂钓点-Avidya ForestVimara Village北 | Normal | Medaka、True Fruit Angler、Sandstorm Angler、Sunset Cloud Angler、Lazurite Axe Marlin、Halcyon Jade Axe Marlin | Fruit Paste Bait、Sugardew Bait |  |  |
| Sumeru | D009-Sumeru-垂钓点-Avidya ForestSumeru City南 | Normal | Dawncatcher、Sandstorm Angler、Sunset Cloud Angler、Lazurite Axe Marlin | Fruit Paste Bait、Sugardew Bait |  |  |
| Sumeru | D010-Sumeru-垂钓点-Ardravi ValleyPort Ormos北 | Normal | Crystalfish、True Fruit Angler、Sandstorm Angler、Sunset Cloud Angler、Lazurite Axe Marlin、Halcyon Jade Axe Marlin | Fruit Paste Bait、Sugardew Bait |  |  |
| Sumeru | D011-Sumeru-垂钓点-Ardravi ValleyDevantaka Mountain | Normal | Dawncatcher、True Fruit Angler、Sunset Cloud Angler、Halcyon Jade Axe Marlin | Fruit Paste Bait、Sugardew Bait |  |  |
| Nod-Krai | G001-Nod-Krai-垂钓点-Lempo IsleClink-Clank Krumkake Craftshop北 | Normal | Medaka、Azuregaze Crystal-Eye、Nightgaze Crystal-Eye、Common Axehead Fish、Veggie Mauler Shark | Fruit Paste Bait、Berry Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G002-Nod-Krai-垂钓点-Lempo IsleNothing PassageNorthwest | Normal | Medaka、Azuregaze Crystal-Eye、Nightgaze Crystal-Eye | Fruit Paste Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G003-Nod-Krai-垂钓点-Lempo IsleBlue Amber Lake | Normal | Common Axehead Fish、Frosted Axehead Fish、Blazing Axehead Fish、Veggie Mauler Shark、Neon Mauler Shark | Berry Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G004-Nod-Krai-垂钓点-Lempo IsleNasha TownSouthwest | Normal | Medaka、Common Axehead Fish、Frosted Axehead Fish、Nightgaze Crystal-Eye | Fruit Paste Bait、Berry Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G005-Nod-Krai-垂钓点-Paha Isle月矩力实验设计局北 | Normal | Medaka、Azuregaze Crystal-Eye、Veggie Mauler Shark、Neon Mauler Shark | Fruit Paste Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G006-Nod-Krai-垂钓点-Paha Isle月矩力实验设计局Southeast | Normal | Medaka、Common Axehead Fish、Frosted Axehead Fish、Nightgaze Crystal-Eye | Fruit Paste Bait、Berry Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G007-Nod-Krai-垂钓点-Hiisi IslandLight-Bathed PlatformSouthwest | Normal | Veggie Mauler Shark、Neon Mauler Shark、Azuregaze Crystal-Eye、Nightgaze Crystal-Eye | Berry Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G008-Nod-Krai-垂钓点-Hiisi IslandFrostmoon WorkshopNortheast | Normal | Frosted Axehead Fish、Azuregaze Crystal-Eye、Nightgaze Crystal-Eye、Neon Mauler Shark | Berry Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G009-Nod-Krai-垂钓点-Hiisi IslandFrostmoon Workshop西 | Combat | Medaka、Azuregaze Crystal-Eye、Nightgaze Crystal-Eye | Fruit Paste Bait、Refreshing Lakka Bait | 是 |  |
| Nod-Krai | G010-Nod-Krai-垂钓点-虚海望噩影泽地Northeast | Normal | Medaka、Veggie Mauler Shark、Neon Mauler Shark、Azuregaze Crystal-Eye | Fruit Paste Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G011-Nod-Krai-垂钓点-虚海望Piramida南 | Normal | Medaka、Common Axehead Fish、Frosted Axehead Fish、Veggie Mauler Shark、Neon Mauler Shark | Fruit Paste Bait、Berry Bait、Refreshing Lakka Bait |  |  |
| Nod-Krai | G012-Nod-Krai-垂钓点-烟硌山峰Cliffwatch Camp西 | Normal | Common Axehead Fish、Frosted Axehead Fish、Veggie Mauler Shark、Neon Mauler Shark、Azuregaze Crystal-Eye、Nightgaze Crystal-Eye | Berry Bait、Refreshing Lakka Bait |  |  |
| 霜月 | ZG001-霜月-垂钓点-Ungien's Circle | Normal | Medaka、Frosted Axehead Fish、Azuregaze Crystal-Eye、Nightgaze Crystal-Eye | Fruit Paste Bait、Berry Bait、Refreshing Lakka Bait |  |  |
| Snezhnaya | H001-Snezhnaya-垂钓点-Everfrozen Earth海屑镇 | Normal | Medaka、Charcoal Snowfin、Frostpetal Starbloom Fish、Ruby Starbloom Fish | Fruit Paste Bait、Glimmering Bait |  |  |
| Snezhnaya | H002-Snezhnaya-垂钓点-Everfrozen Earth海屑镇Southwest | Combat | Medaka、Charcoal Snowfin、Moonlight Snowfin、Frostpetal Starbloom Fish、Ruby Starbloom Fish | Fruit Paste Bait、Glimmering Bait | 是 |  |
| Snezhnaya | H003-Snezhnaya-垂钓点-Volkodlak Tundra中部 | Normal | Charcoal Snowfin、Moonlight Snowfin、Iridescent Starbloom Fish、Ruby Starbloom Fish、Frostpetal Starbloom Fish | Glimmering Bait |  |  |
| Snezhnaya | H004-Snezhnaya-垂钓点-Volkodlak Tundra巡猎者木屋北 | Normal | Medaka、Charcoal Snowfin、Ruby Starbloom Fish、Frostpetal Starbloom Fish、Iridescent Starbloom Fish | Fruit Paste Bait、Glimmering Bait |  |  |
| Snezhnaya | H005-Snezhnaya-垂钓点-Volkodlak Tundra凝露镇东 | Normal | Frostpetal Starbloom Fish、Ruby Starbloom Fish、Iridescent Starbloom Fish、Charcoal Snowfin、Cream Snowfin、Moonlight Snowfin | Glimmering Bait |  |  |
| Snezhnaya | H006-Snezhnaya-垂钓点-Volkodlak Tundra凝露镇Northeast | Normal | Medaka、Frostpetal Starbloom Fish、Ruby Starbloom Fish、Charcoal Snowfin、Moonlight Snowfin | Fruit Paste Bait、Glimmering Bait |  |  |
| Snezhnaya | H007-Snezhnaya-垂钓点-Fellfrost Peak汐歌Cave西 | Normal | Medaka、Charcoal Snowfin、Moonlight Snowfin、Iridescent Starbloom Fish、Ruby Starbloom Fish | Fruit Paste Bait、Glimmering Bait |  |  |

</details>

---

# 📬 反馈与Supports

- **Recommended反馈群**：BetterGI v7 群（1029539994）
- **反馈邮箱**：hijiwos@hotmail.com