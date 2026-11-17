## 一、Features概述

### 1. 初始化Recording

- 用于建立药品库存的“基准值”
- 通常在第一次使用或库存发生大幅变化时执行
- 会将当前库存写入【history】

### 2. Recording + 消耗计算

- 在存在初始化Recording的前提下运行
- Auto 查找最近一次初始化Recording
- 计算当前库存相对于初始化时的消耗量
- Recording结果写入【history】
- 消耗结果写入【consumption】

### 3. 纯Recording模式

- 不参与初始化与消耗计算
- 每次运行仅Recording当前库存
- 用于长期留档或手动分析
- 输出至【snapshot】

## 二、输出文件Guide / Instructions

- 三个模式分别输出三个文件，格式为：年月日时分秒-模式-名称-数量，回血和复活药分行Recording。

## 三、Instructions

- 纯Recording模式：运行一次Recording一次，自行操作Recording。
- 消耗对比模式：NormalRecording减去上次初始化Recording，得出消耗量，如果Nope初始化，则Auto 转化为初始化数据。

## 四、Version与环境
- BGI ≥ v0.54

