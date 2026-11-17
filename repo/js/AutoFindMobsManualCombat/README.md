# Auto 寻路\+手动Combat 脚本Guide / Instructions v1\.12

**Author**：吉吉喵

**适配Version**：BGI 0\.64\+

**脚本定位**：半Auto 休闲刷怪脚本，主打**解放手动寻路，自由Combat拾取**。全程Auto Pathing寻怪，抵达Combat点Auto 暂停，交给玩家手动打怪、按需开宝箱、捡材料、收集神通，操作自由、Combat爽快。内置Path哈希校验、Auto CD冷却、运行RecordingFeatures，省心Stable。

## 一、免责声明

1\. 本脚本为玩家个人自制辅助工具，仅用于单机娱乐Learning，仅供BetterGI软件本地使用。

2\. 脚本仅提供Auto 化Pathing辅助，所有操作均由用户自主触发、自主承担使用风险，Author不承担任何因使用本脚本产生的Account问题及相关责任。

3\. 禁止将本脚本用于商业化、倒卖、二次封装商用等违规行为，禁止用于破坏游戏平衡、违规挂机等场景。

4\. 使用过程中因操作不当、Path文件Exception / Error、手动操作失误造成的问题，均由使用者自行负责。

## 二、核心Features

- **Combat节点Auto 暂停**：Auto 识别PathCombat点位，到达Combat位置Auto 暂停脚本。玩家手动打怪结束后，可自由开宝箱、拾取材料、收集神通，操作完成按下暂停键，即可继续运行下一个Path点位。

- **Path哈希校验**：对Path坐标生成唯一哈希值，Path改动Auto 重新适配，仅改名不失效，杜绝损坏、过期Path运行。

- **Auto CD管理**：智能判断材料、怪物Path刷新冷却，Auto 跳过未冷却完成的Path，避免无效重复Pathing。

- **运行Recording缓存**：Auto 留存每条Path的运行时间数据，为CD冷却判定提供精准依据。

## 三、脚本Settings项

### 1\. 暂停按键（virtualKey）

默认 VK\_END（End键）。Combat点位Auto 按下该键暂停脚本，可自行查阅按键文档更换自定义按键。

### 2\. 跳过转换（noReload）

默认关闭：每次启动重新适配Path、适配新按键/新Path。

开启：跳过Path转换，直接读取缓存Path运行，启动更快，适合长期固定Path挂机。

## 四、目录Guide / Instructions

- `pathing/`：放置原始刷怪Path，pathing下的文件夹名参考materialsCD\怪物.txt里面的怪物名，可增自定义名

- `materialsCD/`：材料刷新冷却规则Configuration

- `user/output_combat_convert/`：脚本Auto 生成的可用Path

- `user/content_code_record.json`：Path哈希与按键缓存Recording

- `pathing_record/`：Path运行时长、CDRecording

## 五、使用Precautions / Notes

1\. 本脚本仅Auto Pathing，无Auto Combat。开战点位挂机Zoned Out，Character可能被怪物击杀。

2\. 暂停状态下Character死亡，手动复活后重启脚本即可继续运行。

3\. 不想运行某条Path，直接中断脚本、删除对应Path文件后重启。

4\. 跑完的PathAuto 进入CD冷却，不会重复运行；使用问题可截图咨询答疑。

5\. 仅Supports6层以内Path文件夹层级，No Combat节点的纯采集Path会Auto 跳过。

6\. Combat结束后，可按需开宝箱、拾取材料，按下一次暂停键即可继续运行下一个点位。

## 六、后言

本脚本目前处于测试阶段，欢迎反馈问题至 QQ 频道号：bettergiv1。

## 七、Changelog

**v1\.0**：实现CombatAuto 暂停、Path哈希校验、Auto CD冷却、自定义按键、运行Recording缓存全套Features

**v1\.12**：修复CD计算bug

*以上内容由豆包生成。*
