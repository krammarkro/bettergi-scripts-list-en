### Medicine Consumption Stats脚本Instructions
## 📋 一、Usage
本脚本需在锄地All-in-One Run流程前后各运行一次（前置=Recording药品初始数量，后置=对比统计消耗），开启通知后即可Roger That药品消耗情况推送。Supports两种接入方式：
1. **直接添加脚本**：在锄地All-in-One RunJS的前置/后置任务中分别添加本脚本
2. **Configuration组方式**：新建两个Configuration组并添加本脚本，在All-in-One Run中分别添加前后两个Configuration组

## 🛠️ 二、环境与工具要求
### 工具要求
BGISupports两种Auto Taking Medicine方案：
- **茶包版BGI**（可选）：公版BGI默认关闭Auto Taking MedicineFeatures且无法通过脚本开启，茶包版BGI可开启此Features
- **锄地All-in-One Runjs**（Recommended）：在锄地All-in-One RunjsSettings中填写「使用复活药数量」和「使用回血药数量」，即可开启Auto Taking MedicineFeatures

### 系统Configuration要求
1. **游戏分辨率**：固定1920×1080（不可修改，影响OCR识别区域定位）
2. **游戏和jsSettings**：
   - 需装备「便携营养袋」
   - 启用「筛选模式」和「综合模式」时需要填写完整的药名

## 📥 三、获取茶包版BGI
1. 仓库地址：[https://github.com/kaedelcb/better-genshin-impact](https://github.com/kaedelcb/better-genshin-impact)
2. 下载方式：登录GitHub账户 → 进入Actions页面 → 下载workflow产物
3. Actions链接：[https://github.com/kaedelcb/better-genshin-impact/actions](https://github.com/kaedelcb/better-genshin-impact/actions)

## ⚙️ 四、参数ConfigurationGuide / Instructions
| 参数项 | 类型 | 填写要求 | 默认值 | 核心Guide / Instructions |
|--------|------|----------|--------|----------|
| **runMode** | 下拉选择 | 三选一：「营养袋模式」/「筛选模式」/「综合模式」 | 营养袋模式 | 营养袋模式：读取便携营养袋内药品；筛选模式：通过Inventory筛选搜索药品；综合模式：营养袋模式+筛选模式结合 |
| **initSelect** | 复选框 | 仅初始化/重置时临时勾选 | false | 勾选后运行脚本会删除当日同名Recording，重新初始化数据（使用后务必取消） |
| **userName** | 文本输入 | 1-20字符，仅Supports中英文、数字 | 默认账户 | 多账户区分核心，违规名称Auto 替换为默认账户 |
| **refreshTime** | 文本输入 | 0-24之间，Supports一位小数 | 4.0 | 自定义每日统计周期分界点（如4.5=4:30），错误值Auto 修正为4.0 |
| **loadDelay** | 文本输入 | 非负整数（单位：毫秒） | 800 | 界面打开/Switch的等待延迟，低Configuration设备可适当增大 |
| **stepDelay** | 文本输入 | 非负整数（单位：毫秒） | 500 | OCR识别/输入药名前的短暂等待，保证识别Stable性 |
| **autoRefillRecovery** | 复选框 | Auto 补充回血药开关 | false | 开启后当回血药数量低于阈值时，Auto Go toCooking锅制作回血药 |
| **refillThreshold** | 文本输入 | 正整数 | 100 | 回血药数量阈值，低于此值时触发Auto 补充 |
| **refillCount** | 文本输入 | 正整数 | 20 | Auto 补充回血药的数量（1-99之间） |

### Configuration优先级
脚本运行时参数读取规则：`自定义Configuration > 默认值`，参数错误时Auto 兜底为默认值并输出WarningLog。

## 🔄 五、操作流程（适配双模式）
### 场景一：首次使用
1. 启用筛选模式需要完成参数Configuration（填写药品名称），启用营养袋模式则需要营养袋装备两种药品
2. 确认游戏分辨率1920×1080，便携营养袋已装备
3. 运行脚本，Auto 执行：
   - 校验账户名合法性 → 打开Inventory → 按选定模式识别药品数量
   - 在`assets/`目录生成「账户名.txt」Recording文件
4. Roger That「今日初始化完成」通知，首次Configuration完成

### 场景二：日常使用
#### 营养袋模式
- 脚本Auto 打开Inventory→进入小道具→读取便携营养袋内回血/复活药数量
- 无Manual Required筛选，识别速度更快，依赖便携营养袋装备状态

#### 筛选模式
- 脚本Auto 打开Inventory→进入食物分类→筛选搜索指定药品→读取数量
- 无需装备营养袋，适配未Configuration营养袋的场景，识别流程稍长
- 处理所有填写了名称的药品（回血/复活/攻击/防御/Other/增伤/抗性/额外，共8种）

#### 综合模式
- 脚本Auto 执行：营养袋模式识别回血/复活药 + 筛选模式识别攻击/防御/Other/增伤/抗性/额外药
- 结合两种模式优势，Supports全类型药品统计
- 回血药和复活药通过营养袋模式获取，攻击药、防御药、Other药、增伤药、抗性药、额外药通过筛选模式获取

#### 通用规则
- 每日首次运行（自定义refreshTime后）：Recording为当日初始值
- 后续运行：对比初始值计算消耗/新增（正数=消耗，负数=新增）
- 每次运行Auto 保存Recording，仅保留30天内数据，过期Auto 清理
- 只Recording数量大于0的药品数据

### Auto CookingFeatures
当开启「Auto 补充回血药」Features后，脚本会在检测到回血药数量低于阈值时，同时有消耗数量，Auto 制作回血药：
- **触发条件**：`autoRefillRecovery`开启 且 回血药数量 < `refillThreshold`
- **执行流程**：Go toMondstadt炉子 → 打开Cooking锅 → 搜索并制作指定的回血药
- **制作数量**：每次Auto 制作 `refillCount` 个回血药
- **适用场景**：适用于一天只运行两次JS的情况（如早晚各一次），多次运行不Recommended开启此Features，避免Recording错误
- **Precautions / Notes**：
  - 复活药等Other药品暂不SupportsAuto 补充
  - 回血药需要解锁Auto CookingFeatures，否则无法Auto 补充

### 场景三：更换药品/重置统计数据
1. 在Settings中勾选`initSelect`选项
2. 确认药品名称已更新为新名称（如需更换）
3. 运行脚本一次，Roger That「强制初始化完成」通知
4. **立即取消`initSelect`勾选**（避免后续运行重复初始化）

## 📊 六、核心机制（新增/补充）
### 1. 自定义统计周期计算规则
以`refreshTime`为分界点，脚本Auto 判定统计范围：
- 当前时间 < 当日refreshTime：统计「昨日refreshTime → 今日refreshTime」数据
- 当前时间 ≥ 当日refreshTime：统计「今日refreshTime → 明日refreshTime」数据
示例：refreshTime=4.5（4:30），当前时间3:00 → 统计昨天4:30至今；当前时间5:00 → 统计今天4:30起。

### 2. Recording文件格式
```
时间:202X/XX/XX XX:XX:XX-【药品名称】-【数量】
时间:202X/XX/XX XX:XX:XX-【药品名称】-【数量】
...
```
每条Recording包含时间戳+药品名+数量，Supports8种药品类型：
- 回血药
- 复活药
- 攻击药
- 防御药
- Other药
- 增伤药
- 抗性药
- 额外药

**Note**：只生成数量大于0的药品Recording，保证数据有效性。

## 📝 九、Changelog

### 2026-09-17
1. 修改了一下ocr范围
2. 增加筛选药品选项