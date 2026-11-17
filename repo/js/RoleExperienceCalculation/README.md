# 《原神Character经验计算脚本》Instructions
## 一、Precautions / Notes
* 联机状态无法运行
* ocr识别会小概率出现偏差，重新运行即可
* 脚本生成的报告文件仅供作为参考，实际请按游戏为准

## 二、脚本概述
1. Auto 识别指定Character的当前等级和经验值
2. 计算升级到目标等级所需的总经验值
3. 可选：结合Inventory经验书进行统合计算
4. Auto 生成经验计算报告并保存为文本文件

## 三、Usage和Configuration参数Guide / Instructions
1. 需在调度器的Configuration组中点击 “+添加 → JS脚本” ，找到本JS脚本后加入Configuration组。
2. 加入Configuration组后鼠标右键脚本， 修改JS脚本自定义Configuration。
3. 脚本运行完成无Exception / Error后，会在脚本根目录下的 “test” 文件夹内创建文本文件，
文件名为exp_result_YYYYMMDD_HHMMDD，即exp_result_年月日_时分秒。

脚本的"js自定义Configuration"Settings：

    1. 目标Character (必填)：
        - 格式：单个Character名，或多个Character用逗号分隔（中英文皆可），Supports使用别名
        - 示例："Keqing,Ganyu,帝君"
    2. 目标等级 (必填)：
        - 格式：整数，表示目标等级
        - 示例：90 (范围：2-90)
    3. 结合当前Inventory拥有的经验书计算 (可选)：
        - 将扫描Inventory内经验书并统合计算

## 四、脚本文件结构
* main.js：主要的脚本文件
* manifest.json：脚本Configuration文件
* settings.json：用户Configuration文件
* test/：存放脚本运行后保存的文本文件
* lib/：存放脚本依赖的JS模板文件
* assets/：存放模板图片

## 五、关于脚本运行后保存的文本文件
以下是示例文本内容：

    === 原神Character升级所需的经验Recording [2026/1/1 16:05:06] ===

    ===【Character数据】===
    【Jahoda】
        当前等级：1级
        当前经验：0
        升级至90级所需经验：8362650
    
    ===【经验书数据】===
        Hero's Wit：
        数量：300
        总经验值：6000000
    
        Adventurer's Experience：
        数量：561
        总经验值：2805000
    
        Wanderer's Advice：
        数量：100
        总经验值：100000
    
    === Recording结束 ===
    总计Character数：1 | 所有Character升至90级总计所需经验：8362650
    Inventory经验书种类数：3 | 总计经验值：8905000
    经验盈余：542350（超出需求）
    
    当前世界等级：9
    单次启示之花奖励（20原粹树脂）：
     Hero's Wit：4~5本
     Adventurer's Experience：6~7本
    
    ================ 计算结果 ================
    当前Inventory内经验书已Happy经验需求，无需刷取