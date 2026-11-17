# Escoffier厨艺机关

## 项目简介
本脚本用于Auto 操作Escoffier厨艺机关，通过Barbara的攻击动作为机关充能，实现Auto 获取Food / Dishes的Features。脚本支持周期性执行，可根据需要Settings为每周一执行或每天执行。

## Author信息
- **Author**：LCB-茶包
- **联系方式**：QQ 119996800

## Instructions

### 必要Configuration
1. **队伍Settings**（必填）：使用前请在Configuration中Settings要Switch的队伍，否则脚本会Auto 结束任务
2. **队伍编排**：请确保Switch的队伍中：
   - 3号位：Escoffier
   - 4号位：Barbara

### 执行模式
- **周一执行**（Recommended）：选择"是"，脚本会Auto 判断是否为星期一从而执行
  - Escoffier厨艺机关每周限制10个Food / Dishes，周一更新CD
  - 直接加入调度器即可Auto 运行
- **每天执行**：选择"每天执行"为每次都执行
- **禁用模式**：选择"否"为禁用脚本

### Features特性
- **Auto 检测**：脚本会Auto 判断是否获得10个Food / Dishes后Auto 退出
- **时间控制**：一般60秒完成，最大超时默认100秒（可自定义Configuration）
- **多Account支持**：支持UID禁用模式，可Settings不执行的UID
  - 格式：用 `/` 分隔多个UID，如 `12345/99999`
  - 适用于多个Account但部分AccountNopeEscoffier的情况

## 技术原理
脚本通过Barbara的攻击动作为Escoffier厨艺机关充能，实现Auto 化Food / Dishes制作过程。

## Precautions / Notes
- 脚本可能存在误差，建议在测试环境中先行验证
- 执行时间受网络环境和设备性能影响

## 反馈与支持
如遇到错误或问题，请联系：
- QQ：119996800

## Changelog

### v1.3 (2025-05-12)
- 更改UID识别方法（适配原神UI改变）
- 修改超时默认时间

### v1.2 (2025-05-10)
- 首次发布Version

