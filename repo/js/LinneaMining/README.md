# LinneaMiningAll-in-One Run

专用于运行Linnea自瞄Mining的脚本，不分矿种，只挖Stable刷新的Minerals。  
自带月卡监听，可跨4点执行，但月卡跳出时脚本仍在执行，可能会引起故障。  
本脚本不会提供过多Settings项，仅保留必要Settings，最大程度限制Settings数量。

## Supports地区

| 地区   | 状态     |
|------|--------|
| Nod-Krai | ✅ 已Supports  |
| Mondstadt   | 🚧 计划中 |
| Liyue   | 🚧 计划中 |
| Inazuma   | 🚧 计划中 |
| Sumeru   | 🚧 计划中 |
| Fontaine地表 | 🚧 计划中 |
| Natlan   | 🚧 施工中 |

## Guide / Instructions

说在最Starting Up：LinneaMining需要识别元素视野下的黄色岩元素属性Minerals，原神Settings项开的过低会导致黄色变浅，识别率下降，在足够运行的情况下请不要为了节省微乎其微的耗能将Settings调的过低

其它：
- 队伍中必须包含**Linnea**，不建议在**Nod-Krai**地区携带**Columbina**，部分矿点的犀牛会影响Mining。
- 请Configuration好Auto Combat策略，建议关闭Combat后的Auto 拾取，Combat点位仅为必经之路或高收益处。
- 若Observing到部分点位射一箭无法Happy挖掘全部，请反馈给我（如果漏的是铁矿不会考虑，被小动物挡住也大概率不会修改）
- 有一部分铁矿点位位置较为刁钻，加之铁矿这种Minerals本身较无用，将不会收录在本脚本的Route内，同理，其它个别位置刁钻的Minerals点位也不会专程Go to。

## 未来

> 注：未来的部分逻辑会在**最大程度减少Configuration项**的基础上开发，可能会参考[矿产资源批发](https://bgi.sh/?type=js&path=AbundantOre)。  
> 考虑到运行时长，不会Supports多Account

> 又注：当前脚本仅为先行版，作占位避免撞车，因此缺少大部分Route，且Route暂未深度优化。所有国家都补全时将变更为正式版。
