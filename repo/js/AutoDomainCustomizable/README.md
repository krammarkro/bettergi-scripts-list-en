# 传送并Auto Domain (增强版)

本脚本为 **BetterGI** 自带脚本的增强Version。
允许用户直接在脚本Settings中自定义“刷取次数”、“树脂类型”及Other高级参数，Supports周期性素材刷取，无需修改 BetterGI 全局Settings。

---

⚠️有任何问题 **务必** 先阅读错误信息，依照错误信息指示修改Settings，并确保您已 **完整阅读** 本Guide / Instructions。⚠️

遇到无法排除的问题，请将Log去除敏感信息(如Account名称)后，至github提issue上传。
本JS脚本修改者NopeQQAccount。

**强烈建议**先以Debug模式运行后再上传Log。

Nope附上LogRecording的问题将被 **无视** 。

Log默认位置在 `BetterGI\log\` 。

---

## ✨ 主要Features

* **全球时区Auto 换日**：内置时区计算逻辑，Auto 适配游戏服务器换日时间。
* **自定义树脂策略**：Supports指定各类型树脂的使用次数，或选择Auto 刷取至树脂耗尽。
* **智能队伍Switch**：进本前Auto Switch至指定队伍。
* **全Auto 托管**：Auto 传送、进门、Combat及领奖。
* **Auto 处理**：Supports结束后Auto 分解Artifacts。
* **Combat策略选择**：Supports自定义Combat策略文件，可针对不同Domain/队伍Configuration不同的Combat逻辑。
* **Auto 识别限时全开**：Auto 通过OCR识别游戏内的限时全开活动状态。

---

## 🚀 Usage

⚠️ **重要** ：本脚本的参数需要在 **调度器** 中Configuration！

1. 在调度器中添加脚本。
2. **右键点击**脚本并选择 **“修改JS脚本自定义Configuration”**。

### 📌 必填项

* **指定要Go to的Domain**

  * 请在下拉菜单中选择目标Domain。
  * **Note**：【Character天赋】、【武器升级】、【Artifacts】三类选项**互斥** (只能选其中一个)，若同时选择多项，脚本将报错停止。

<br>

* **树脂策略Configuration**

  * **刷取至树脂耗尽 (最高优先级)**

    * 若启用此选项，脚本将**忽略**下方所有具体次数的设定。
    * 依照Configuration中 **树脂刷取顺序** 栏中的树脂种类依序刷取至耗尽，未填写在顺序栏中的树脂 **不会** 进行刷取。

<br>

  * **指定每种树脂刷取数量**

    * 仅在“刷取至树脂耗尽”**关闭** 时生效。
    * 脚本将按照设定的次数进行刷取（若四项均为 0 则不执行Combat）。
    * Supports的树脂类型：
      * **Condensed Resin**
      * **原粹树脂(依照数量计算最少刷取次数)**
      * **须臾树脂**
      * **脆弱树脂**

### ⚙️ 可选项

* **【风险】强制运行**

  * **Features**：勾选后将**忽略日期与限时全开检查**，直接进入Domain。
  * **适用场景**：限时全开Auto 识别有问题或确认游戏有“精通移涌”活动时使用。
  * **Warning**：若当日未开放该素材且无活动，勾选此项将会导致刷错素材。
  * **优先级**：此选项优先级最高，勾选后“Auto 识别限时全开”将无效。

<br>

* **Auto 识别限时全开**

  * **Features**：当日期不匹配时，Auto 通过OCR识别游戏内的限时全开活动状态。
  * **适用场景**：希望脚本Auto 检测活动并在有活动时Auto 进入Domain。
  * **特点**：不需要再手动使用强制运行选项了
  * **限制**：会增加约10-15秒的检测时间,面对特别卡的设备占用时间很长且容易报错
  * **提示**：OCR识别实际上不太Stable，这里只做尽力识别，仍有优化空间，比如识别多处文本进行匹配，或者是利用上识别到的结束时间让不用每次运行都进行OCR，目前主要是测试Stable性

<br>

* **闲时刷取Artifacts**

  * **Features**：当目标素材（武器/天赋）Nope, Not In开放日期且无活动时，Auto Switch到Artifacts刷取。
  * **适用场景**：希望在非素材开放日能消耗树脂刷取Artifacts。
  * **Configuration要求**：需同时Configuration目标素材（武器/天赋）和Artifacts选项。
  * **优先级**：优先尝试刷取目标素材（武器/天赋），条件不Happy时才Switch到Artifacts。
  * **提示**：如果与Auto 识别限时全开同时开启时，OCRDefeat会导致Go to刷取Artifacts

<br>

* **Auto Switch到指定队伍**

  * 输入队伍名称（需与游戏内完全一致，Supports正则表达式），留空则不Switch。

<br>

* **Domain刷取轮数**

  * `0`：刷到体力耗尽或达到指定树脂次数（默认）。
  * `数字`：刷满该场数后强制停止（无论是否还有体力）。

<br>

* **Combat完成后等待时间**

  * SettingsCombatSettlement后的缓冲秒数（默认 5 秒），防止因电脑读取卡顿导致过早退出或识别Defeat。

<br>

* **结束后Auto 分解Artifacts**

  * **Features**：开启后，任务结束前会Auto 执行Artifacts分解逻辑。
  * **分解星级**：可指定分解 **1~4 星** 的Artifacts（需配合下拉菜单Settings）。

<br>

* **启用Debug模式**

  * 开启后会输出更多详细Log信息，用于脚本出错时排查问题。

<br>

* **指定Combat策略**

  * **Features**：指定使用的Combat策略文件，默认根据队伍Auto 选择Combat策略。
  * **策略文件存放位置**：`BetterGI/User/AutoFight/`
  * **用法**：在下拉菜单中选择指定Combat策略，并在Combat策略名称栏中填写文件名（后缀加不加都行，建议不加）,策略文件放在 `User/AutoFight` 下的目录中，（如 `Hu Tao`，实际查找 `User/AutoFight/Hu Tao.txt`,如果位于子目录：例如`AutoFight/群友分享/Hu Tao.txt`则填写`群友分享/Hu Tao`）。
  
  **温馨提示**：部分文件名含有.txt是不能使用的(不是指后缀)，例如.txtaa.txt(或者aa.txt.txt)程序处理完之后会变成aa.txt，导致无法指向原有的文件 ~~但应该没人会用这种文件名~~

<br>

---

## ⏰ 时区Settings

脚本会Auto 读取 BetterGI 的全局Settings来判定今日素材。
请务必Go to **BetterGISettings > OtherSettings > 服务器时区Settings** 进行正确Configuration（如官服/亚服/B服设为 UTC+08:00）。

---

## ⚠️ 已知问题


暂无。


---

## ⚠️ 修改脚本

本脚本采用AI进行生成修改，修改者 **Nope任何编程能力** 。
故在此授权任何人可以在不标注、不通知修改者(RJFAC)的情况下对脚本内容维护、修改、重写、分享、上传、覆盖此脚本的部分或全部内容。

* **Precautions / Notes**
  * 修改脚本前请先进行 **备份** 
  * 修改脚本后请务必 **检查** 以下事项，再提交PR：
      * 更新manifest.json中的version参数
      * 在manifest.json中的authors栏位填上您的名字与github账户链接
      * 更新README.md的Changelog栏位
      * 在README.md关于Author栏位填上您的名字与github账户链接
  * 掉落物名称统一使用最高Rare度（技能突破天赋书4星/武器突破素材5星）。

---

## 📜 Changelog

### v1.1.2 - [RJFAC](https://github.com/RJFAC)
* 修正「菫色之庭」异体字导致的传送问题

### v1.1.1 - [RJFAC](https://github.com/RJFAC)
* 新增Supports7.0SnezhnayaVersion
* 新增天赋技能材料Domain「荒坠的圣迹」与对应选项「「Philosophies of Charity」、「「Philosophies of Fortitude」、「「Philosophies of Glory」
* 新增武器突破素材Domain「妄念的创痕」与对应选项「Triumph of the Pale Star Army」、「Revelry of the Cellared Spiritual Nectar」、「The Frost Emperor's Farewell」
* 新增ArtifactsDomain「逆悬的冰河」与对应选项「Scarlet Proof / Heart of the Furnace」
* Guide / Instructions文档更新
* 修正缺失LiyueArtifactsDomain「山脊守望」与对应选项「Pale Flame / Tenacity of the Millelith」的问题


### v1.1.0 - [lingyu](https://github.com/aaahai00)
* 新增限时全开Auto 识别Features，通过OCRAuto 检测游戏内限时全开活动状态
* 新增"闲时刷取Artifacts"Features，当目标素材Nope, Not In开放日且无活动时Auto 刷取Artifacts
* 修复Combat策略Pathbug，Supports子目录策略文件
* 优化Combat策略名称输入，Auto 处理Path分隔符和 `.txt` 后缀名 ~~(应该Nope人用.txt作为文件名的一部分的吧)~~
* 优化Configuration界面布局

### v1.0.0 - [RJFAC](https://github.com/RJFAC)
* 新增BGI通知
* 新增月之七VersionArtifactsDomain「山风的荆冕」
* 修正Version号以符合SemVer规范

### v0.10 - [RJFAC](https://github.com/RJFAC)
* 调整Combat策略Settings方式
* 在显示Log中新增Guide / Instructions
* Guide / Instructions文档排版
* Debug模式新增显示传入参数

### v0.8 - [风铃](https://github.com/zephyr-bell)
* Supports自定义Combat策略文件

---


## 👨‍💻 关于Author

* **原Author**: [huiyadanli](https://github.com/huiyadanli), iris, 霁
* **修改者**: [RJFAC](https://github.com/RJFAC), [风铃](https://github.com/zephyr-bell), [lingyu](https://github.com/aaahai00)
* **辅助生成**: AI
