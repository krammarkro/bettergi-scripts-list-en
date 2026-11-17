# Food / Dishes制作及Food Processing脚本

本脚本用于Food / Dishes的制作和Food Processing。可根据ConfigurationAuto 选择Food / Dishes和各类Ingredients进行批量制作。

## Features简介

-   Auto Go to指定灶台
-   Auto 筛选并制作指定Food / Dishes，可自定义数量
-   Auto 领取并Processing多种Ingredients（如Flour、Cream、Ham等），每种Ingredients数量可单独Configuration
-   制作完成后Auto 返回主界面并发送通知

## Usage

1. 通过 BetterGI 脚本Settings界面填写各项参数（Food / Dishes名、数量、各类Ingredients数量等）

## 参数Guide / Instructions

| 参数名           | Guide / Instructions           | 默认值 |
| ---------------- | -------------- | ------ |
| foodName         | Food / Dishes名称       | 0      |
| foodNum          | Food / Dishes制作数量   | 1      |
| flourNum         | FlourProcessing数量   | 0      |
| creamNum         | CreamProcessing数量   | 0      |
| smokedPoultryNum | Smoked FowlProcessing数量 | 0      |
| butterNum        | ButterProcessing数量   | 0      |
| hamNum           | HamProcessing数量   | 0      |
| sugarNum         | 糖Processing数量     | 0      |
| spiceNum         | SpiceProcessing数量 | 0      |
| crabRoeNum       | Crab RoeProcessing数量   | 0      |
| jamNum           | JamProcessing数量   | 0      |
| cheeseNum        | CheeseProcessing数量   | 0      |
| baconNum         | BaconProcessing数量   | 0      |
| sausageNum       | SausageProcessing数量   | 0      |

## Precautions / Notes

-   请确保游戏窗口分辨率为 16:9，否则可能点击异常
-   脚本运行期间请勿手动干预，以免流程异常
-   由于是模拟点击，请保证材料的充足，避免造成Processing错误的问题

## 结束

脚本执行完毕后会Auto 返回主界面并发送“Cooking脚本结束”通知。

---

如有问题或建议，欢迎反馈交流！

## Changelog

### 1.3（20250709）

-   优化灶台Path
-   优化灶台交互
-   优化未进入Cooking界面导致的一系列问题
