# Amethyst Lump之Claymore矿闻录 Precautions / Notes
## 一、前言
- 本地图追蹤以Inazuma、Enkanomiya 解谜全解 与 宝箱Full Collection 情况下制作
- 制作脚本时，以**The BellNoelle**作为行走位
- 部份地图追蹤會使用Mavuika趕路
- 队伍 : Noelle、Mavuika、Escoffier、Barbara

- 预期用时 1小时35分~40分 / 235~275 个

## 二、Configuration简介
- 生存位技能 : Barbara
- CD : `300`

- 以下为Combat脚本

    ```
    Noelle e
    Columbina attack(0.01),keypress(q),attack(0.2),e,wait(0.2),attack(0.4),keypress(e),charge(0.2),keypress(q),charge(0.12),attack(0.08),keypress(e),keypress(q),w(0.01),attack(0.2),keypress(e),keypress(q)
    Linnea attack(0.18),keypress(q),wait(0.1), ready,attack(0.05), e,attack(0.65), keypress(q),wait(0.1) ,keypress(q),attack(0.1)
    Mavuika attack(0.01),e
    Escoffier e,wait(0.26),attack(0.15),wait(0.26),keypress(q),keypress(q),wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.2),keypress(q),attack(0.01)
    Barbara attack(0.2),wait(0.3),keypress(e), wait(0.2),keypress(e), click(middle), keypress(q),wait(0.2), keypress(q),keypress(e),wait(0.2), keypress(q) ,attack(0.6),charge(0.6),keypress(e),wait(0.3)
    Mavuika check,q
    Rosaria e,attack(0.4),keypress(q),attack(0.4),keypress(q),e
    Dehya e, attack(0.3), keypress(e), wait(0.3), wait(0.3)
    Noelle e,check,q,ready,charge(2.3)
    Kaedehara Kazuha attack(0.01),wait(0.25),e(hold),click(middle),wait(0.48),attack,wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.3),keypress(q),wait(0.1),keydown(E),wait(0.55),keyup(E),click(middle),wait(0.45),attack,w(0.01),wait(0.19)
    ```

- 開啟 更快檢查結束戰鬥
- 自動撿取掉落物 : 關閉
- 戰鬥超時為`45`秒
- **Combat脚本 与 Combat超时时间 请以个人配队练度及实力自行调整**


## 三、预期数量

- **Narukami Island** : 42
  - Narukami Island No Combat = 27
  - Narukami Island 有Combat = 15
- **Kannazuka** : 35
  - Kannazuka No Combat = 29
  - Kannazuka 有Combat = 6
- **Yashiori Island** : 27
  - Yashiori Island No Combat = 23
  - Yashiori Island 有Combat = 4
- **Watatsumi Island** : 24
  - Watatsumi Island No Combat = 20
  - Watatsumi Island 有Combat = 4
- **Seirai Island** : 35
  - Seirai Island No Combat = 27
  - Seirai Island 有Combat = 8
- **Tsurumi Island**   : 26
  - Tsurumi Island   No Combat = 24
  - Tsurumi Island   有Combat = 2
- **Enkanomiya** : 46
  - Enkanomiya No Combat = 20
  - Enkanomiya 有Combat = 26

**预期总计：235 个**


**去除Combat脚本 (-67) = 168个**