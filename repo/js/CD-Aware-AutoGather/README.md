# Features特点

- Auto 同步获取你订阅的地图追踪任务
- Auto 匹配各类材料的CD，Supports联机模式（会识别是在谁的世界进行采集）
- 可识别Inventory物品数量，并按设定的目标数量按需运行
- 方便的材料选择界面，并Supports按地区、按类别批量选择
- 可Settings一个或多个不运行的时间段
- 采集过程Auto Switch合适的队伍

**若脚本有问题，可[点击此处进行反馈](https://github.com/babalae/bettergi-scripts-list/issues/new?template=bug_report.yml&script-name=CD-Aware-AutoGather:2.9.0&additional-info=保留此行以便通知Author:%20@Patrick-Ze%0A%0A---%0A)**

# 使用前准备

需要你已经进行过地图追踪订阅。建议在脚本仓库的`地图追踪`中直接点击`Local Specialties`、`Minerals`、`Food and Alchemy`右边的`订阅`按钮订阅类别下所有Route。

（今后的Version不再需要创建符号链接，也不再与`Auto 更新已订阅的脚本`Features存在协作问题）

# 运行模式

## 1. 扫描文件夹更新可选材料列表

扫描你已订阅的地图追踪任务中`Local Specialties`、`Minerals`、`Food and Alchemy`三大类下的材料，并更新脚本可用的Configuration菜单。

运行后，再次打开右键的`修改JS脚本自定义Configuration`，将看到新增了多个Configuration项。

完成扫描后会Auto Settings下次的脚本运行模式为`采集选中的材料`。

## 2. 采集选中的材料

运行此模式后，将按照你勾选的条目，执行相应的采集任务。每执行完一条jsonRoute后，将会计算它的下次刷新时间并写入`record`文件夹下的Recording文件。下次运行脚本时，未刷新的Route将Auto 跳过。

采集过程中，如果所有材料均达到了你Settings的目标数量，或者到达你Settings的不执行时间段，会Auto 停止运行。

可以同时勾选多种材料，会逐个进行采集。

此模式下有这些选项可以Configuration：

### 基本Configuration

| 选项 | Guide / Instructions |
| ---- | ---- |
| 按关键词筛选材料Route | 默认为黑名单模式。此时，文件Path中含有任意一个关键词的Route，在扫描时会被忽略。Other模式见后文 |
| Settings首选队伍名称 | 执行采集任务前Switch到指定的队伍，未Settings则不Switch。 |
| Settings备选队伍名称 | 首选队伍缺少对应的采集Character时使用。<br>两支队伍的名称不要存在包含关系，例如不能一支叫`特产`一支叫`特产备选` |
| Nope, Not In以下时间段内运行 | 字面意思。如果脚本启动时间在设定的时间段内，会立即终止；如果运行过程中进入设定的时间段内，也会停止后续Route。SupportsSettings多个时间段，用空格分隔即可，比如`05:20-09:28 21:28-00:20` |
| 物品采集数量目标 | 填写目标数量，留空表示不限制。也可以Settings为`csv`，将按csv文件的Configuration详细设定不同材料的目标，具体见后文。`All-in-One Run`等特殊类型会忽略此Configuration项 |
| 使用指定的Account名保存运行Recording | 留空时，将Auto 识别UID，将其作为Account名Recording材料刷新时间。你也可以主动填写Account名称（不Recommended），会导致联机互采时（例如大小号）无法正确维护材料刷新时间，建议仅在你遇到脚本无法Stable识别你的UID时填写 |

### 材料采集Configuration

这部分Configuration分为4个大类，根据你订阅的Route，可能只会出现其中的部分Configuration。

为了方便用户查找：

- “地区”类型的选项，是按照在游戏中开放的顺序排序的。
- 每个小类别下的选项，是按照拼音的先后顺序排序的。

**【常用采集选项】**

开发了按类别、按地区批量选择的Features，并和常用材料汇集到了一起以方便使用，如图所示。

`按大类选择`和`按地区选择Local Specialties`都是批量选择。批量选择和后面的具体项选择可以结合使用，实现灵活的采集目标设定。

比如勾选 `按大类选择`的Minerals + `按地区选择Local Specialties`里的Mondstadt + `单独选择Local Specialties`下的Inazuma地区的Sakura Bloom。

![pic-1](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-1.png)

**【单独选择Local Specialties】**

![pic-2](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-2.png)

**【Food and Alchemy】**

![pic-3](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-3.png)

**【对于具有多VersionRoute的物品，选择要使用的Route】**

如果你为某种材料订阅了多个Version的Route，可以在这里进行选择其中的一个或多个选项。

如果你Nope指定Route，会默认执行第一项的Route。

![pic-4](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-4.png)

### 队伍ConfigurationRecommended

采集任务可能用到的元素共有`火水雷风`4种，此外还有Mining类以及Nahida两个类型，可以考虑建立两支队伍`矿纳水雷`和`矿纳火风`，即可Happy所有采集任务的需要。如果你有Linnea，Recommended让她作为Mining位Character。

Configuration好两支队伍后，脚本会在执行Route前计算所需Character，如果当前队伍不Happy要求，会Auto Switch到另一支队伍。

Note：队伍SwitchFeatures在联机模式下无法执行，因此联机采集时请先调整好队伍中的Character。

# 进阶用法

### 1. 不想每次订阅材料Route后都要在脚本Settings中再勾选，怎么办？

利用好`按大类选择`选项。你可以勾选上全部三个大类（或者你实际需要的类别），然后，只要在BGI本体里订阅Route即可。

### 2. 怎么清除运行Recording（重置材料刷新时间）？

运行Recording保存在脚本所在Path的`record`文件夹中，以UID（或者用户指定的名字）作为Account文件夹。打开子文件夹后，删除对应材料的txt文件即可。

### 3. `按关键词筛选材料Route`的进阶用法

如前面Configuration描述中所述，此选项默认以黑名单模式运行，Settings的关键词即为黑名单，在扫描时会被忽略。可以在选项的开头加上`include:`，将Switch为以白名单模式运行，例如`include:Without Nahida`将只扫描含有"Without Nahida"字样的Route。

或者更进阶的，使用`regex:`开头，将完全使用你Settings的正则表达式进行筛选。如果你不了解什么是正则表达式，Guide / Instructions你大概率也不需要这种方式。

使用该选项Settings的进阶用法时，希望你充分理解了自己的Settings会产生什么样的效果。

### 4. 在`物品采集数量目标`选项中，如何为不同物品Settings不同的目标？

如果你的目标Compare简单，比如想把Local Specialties都设为168，Minerals都设为100，那只要在调度器中重复添加本脚本，然后分别Settings不同的数量目标即可。

如果你有更细致的需要，请将该选项Settings为`csv`，然后打开record文件夹下对应Account的子文件夹，会找到一个名为`采集目标`的csv文件。

你可以用Excel或者WPS等打开此csv文件，打开后就是一个表格（如果你了解csv文件格式，也可以用任意文本编辑器打开，不过不Recommended）。表格内容示例如下：

| 物品             | 目标数量 |
| -------------- | ---- |
| Local Specialties           |      |
| Minerals             |      |
| Food and Alchemy          |      |
| Local Specialties\\Liyue       |      |
| Local Specialties\\Inazuma       |      |
| Minerals\\Condessence Crystal        |      |
| Minerals\\Rainbowdrop Crystal        |      |
| Food and Alchemy\\Crystalfly      |      |
| Food and Alchemy\\Pinecone      |      |
| Local Specialties\\Liyue\\Noctilucous Jade  |      |
| Local Specialties\\Liyue\\Starconch   |      |
| Local Specialties\\Inazuma\\Sakura Bloom |      |
| Local Specialties\\Sumeru\\Rukkhashava Mushrooms  |      |

默认情况下`目标数量`这一列是空的，填写具体的数字，保存文件后关闭Excel（或者Other你用来编辑csv的工具）。然后，再次运行脚本即可。

**如你所见，这个csv表格也具有和脚本选项中相似的层次关系。 是的，数量是按层次继承的~** 🎉

- 如果低层次的材料NopeSettings目标，则会Auto 尝试较高层次所设定的数量
- 如果向上遍历所有层次都Nope目标数量，则表示不限制数量
- 数量为`0`将不进行采集

利用好脚本Settings中的批量选择Features和这个层次关系，可以轻松实现灵活的采集目标。比如：

- 希望Inventory材料能立即把一个Character拉到90级，于是在`按大类选择`中勾选了Local Specialties，并将Local Specialties类别的数量Settings为168
- 但是，又觉得不会再用到Rukkhashava Mushrooms，所以把`Local Specialties\Sumeru\Rukkhashava Mushrooms`的数量Settings为0
- Liyue的特产希望多采集一点，那就把`Local Specialties\Liyue`的数量增加了一点到199
- 还想做用`Snow on the Hearth`填满Inventory，那就把对应的特产`Local Specialties\Inazuma\Sakura Bloom`Settings为9999
- 想要随时能锻造武器，于是于是在`按大类选择`中勾选了Minerals，并将Minerals类别的数量Settings为50
- 不想抓Crystalfly，随便设个100个Crystalfly吧
- 对了，还有每周参量质变仪要用的Mint，要不就2倍数量吧，300
- ……

选好材料和数量，Configuration好队伍，然后把脚本加到你的每日Configuration组或All-in-One Run中，从此实现Inventory自由。


# 致谢

此脚本的2.0Version进行了重写，基于新的API重新设计了主要逻辑，以解决此前我想要处理却不能的痛点。在此，

- 诚挚致敬[鸭蛋老师](https://github.com/huiyadanli)和BGI的诸位贡献者，是各位使我的Teyvat之旅得以苟延残喘

- 得益于[FishmanTheMurloc](https://github.com/FishmanTheMurloc)的鼎力相助，脚本才能实现无图的批量材料扫描

- 受惠于[JamisHoo](https://github.com/JamisHoo)的Configuration界面优化，使得更便捷的材料选择成为可能

- Thank You[this-Fish](https://github.com/this-Fish)的改进，基于坐标判断是否更新Recording、将材料是否刷新的检查提前都是沿袭的TA的思路

- 参考了[吉吉喵](https://github.com/JJMdzh)的Inventory扫描，增加了使用补充OCR的方式识别物品数量的机制

最后，要特别Thank YouKamisato Ayaka，是她陪伴了我的Teyvat之旅。在弃坑之后，唯有这份牵挂，支撑着我重新回到这里。

Nope她就Nope今天的这个脚本。

![in-a-league-of-her-own](https://ayaka20.ggff.net/img/ayaka.png)
