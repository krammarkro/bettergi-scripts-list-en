## Precautions / Notes

**批量采集前，请对用到的Path进行预测试，避免因Route卡死或OtherException / Error情况导致空跑**

目前脚本已Supports识别Inventory内木材数量（默认关闭），可在自定义Configuration中指定木材种类进行识别（**存在无法识别的情况**）

开启Inventory检测后，会导致自定义Configuration中填入的砍伐数目**不生效**，且**无法识别的木材不进行采集**

脚本内置的Path仅供参考，随着软件及地图的更新，可能**并非最佳**采集Path，如有更好的Path，欢迎贡献

目前脚本已Supports7.0Version之前的全部木材，清单如下：`Birch Wood Cuihua Wood Pine Wood Fragrant Cedar Wood Fir Wood Bamboo Segment Sandbearer Wood Yumemiru Wood Maple Wood Aralia Wood Otogi Wood Brightwood Karmaphala Wood Adhigama Wood Athel Wood Tamarisk Wood Platanus Wood Linden Wood Ash Wood Cypress Wood Torch Wood White Chestnut Oak Wood Explosive Wood Mountain Date Palm Wood Peach Palm Wood Silver Fir Wood Hazel Wood Pedunculate Oak Wood Alder Wood Snow Poplar Wood White Birch Wood Bluebeech Wood Larch Wood`

## 原理Guide / Instructions

5.2Version后，王树瑞佑的使用冷却时间从15秒降至5秒

退出重新登陆会刷新木材采集时间

当采集到第11棵树的时候，第1棵树会刷新，采集到第12棵树(第1棵树)的时候，第2棵树会刷新，依次类推

## 循环Guide / Instructions

* 未标注：从Teleport WaypointStarting Up采集，重复循环该Path

* 大循环：从Teleport WaypointStarting UpGo to采集区域，仅执行1次

* 循环：不含Teleport Waypoint，减少地图传送及Pathing时间，执行完1次大循环后，重复循环该Path

因采用不同配队时，采取不同的循环方式耗时上有一定差距，故部分木材预留了循环Path和未标注Path，请根据实际情况自行选择，在[main.js](main.js)的`pathingMap`中修改即可。
