# 🦌Lauma🕊少女Raw Meat采集

## 📖 脚本Guide / Instructions

本脚本可利用Lauma/哥伦比亚能够吸引Nod-Krai小动物，并让獾给自己挖肉的特性，榨干Nod-Krai生态的每一份养料。  
本脚本与纯地图追踪的Version的主要区别为Auto 根据天气，等待雨天结束，并能够直接判断你队伍里是否有Lauma🦌或Columbina🕊。  
Raw Meat资源每天的刷新时间为击杀后12小时，如有需要可自行规划采集

## 🚀 运行效率

- **理论收获**：13分钟可收获最多85个Raw Meat
- **实际收获**：常态下12分钟拾取约75个Raw Meat

## ⚠️ 运行须知（必看）

1. **Character要求**：运行前请确保队伍中有「Lauma」/ 「Columbina」与「Kaedehara Kazuha」，并在`调度器`Settings中将`Lauma`/ `Columbina`Settings为行走位   

![Settings](assets/settings.png)

2. **Route冲突**：运行前请确保今天Nope跑过`Rainbowdrop Crystal`Route和`Frostnight Scion`Route，这些Route与Raw MeatRoute存在重叠
3. **Teleport Waypoint解锁**：苔古荒原中间的Teleport Waypoint处有一个需要Searching10个机器人才能解锁的飞高高装置，请解锁它
4. **游戏窗口**：请确保游戏窗口为1920x1080分辨率以减少问题发生的概率（2560暂时没发现问题）

## ⚙️ Settings选项

### 启用潮湿状态检测
- **Features**：Auto 检测游戏中的潮湿状态（下雨等）
- **作用**：潮湿状态下小动物会消失，脚本会Auto 调整时间到非潮湿状态
- **建议**：保持启用状态

### 最大等待次数
- **Features**：Settings潮湿状态检测的最大尝试次数
- **默认值**：5次

### 运行High RiskRoute
- **Features**：是否运行包含Frostnight Scion的容易暴毙Route
- **Guide / Instructions**：High RiskRoute物资丰厚，可选择性关闭
- **默认**：启用

### 队伍名称
- **Features**：Settings要Switch到的队伍名称
- **Guide / Instructions**：脚本Starting Up时会Auto Switch到指定队伍，务必关闭`调度器`Settings中的`Switch Party`
