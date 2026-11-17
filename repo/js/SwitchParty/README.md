# Switch Party（BgiTools版）

## 简介

该脚本用于 BetterGI 中Auto Switch原神队伍。Supports两种加载模式：

- **输入加载**：手动在Settings中填写队伍名称，脚本直接Switch。
- **bgi_tools加载**：通过 BgiTools HTTP 接口查询当前 UID 对应的队伍信息，再Auto 完成Switch。(需要JS HTTP权限Supports)

## Features特点

- Supports输入加载和 bgi_tools 加载两种模式
- Auto 获取当前游戏 UID，并通过 HTTP 接口查询目标队伍
- Switch PartyDefeat时Auto 传送至Statue of The Seven并重试
- Supports自定义 Token 名称和值
- 完善的LogRecording和错误通知

## 目录结构

```text
SwitchParty/
├── main.js                 # 脚本入口
├── manifest.json           # BetterGI 插件清单
├── settings.json           # Settings界面定义
├── assets/
│   └── ui/main_ui.png      # 主界面识别模板图
└── utils/
    ├── tools.js            # 通用工具类
    └── bgi_tools.js        # BgiTools API 请求封装
```

## ConfigurationGuide / Instructions

| Settings项 | 类型 | 默认值 | Guide / Instructions |
|--------|------|--------|------|
| `auto_load` | 下拉选择 | `输入加载` | 加载模式，可选“输入加载”或“bgi_tools加载” |
| `team` | 文本框 | 空 | 队伍名称，适用于“输入加载”模式；留空表示不Switch Party |
| `type` | 文本框 | 空 | 分组类型，适用于“bgi_tools加载”模式，会作为请求参数传给接口 |
| `bgi_tools_uid_team_api` | 文本框 | `http://127.0.0.1:8081/bgi/uid/team` | BgiTools HTTP API 地址 |
| `bgi_tools_token` | 文本框 | `Authorization= ` | BgiTools 鉴权 Token，格式为 `Token名=Token值` |

### 输入加载使用示例

- 加载模式：`输入加载`
- 队伍名称：`1`（请填写游戏内实际的队伍名称）
- Other字段可留空

脚本会直接使用 `team` 作为目标队伍名称，调用 `genshin.switchParty(team)` Switch。

### bgi_tools 加载使用示例

- 加载模式：`bgi_tools加载`
- 分组类型：`独立`（可按需填写，用于在 BgiTools 侧分组）
- BgiTools HTTP API：`http://127.0.0.1:8081/bgi/uid/team` 请部署[bettergi-scripts-tools](https://github.com/Kirito520Asuna/bettergi-scripts-tools)(点击Go to部署) v0.1.9以上Version
- Token 示例：`Authorization=你的Token值`
### bettergi-scripts-tools 使用演示
![demo](./assets/md/bgi_tools_init.jpg)
![js](./assets/md/bgi_tools_js.jpg)

脚本运行逻辑如下：

1. 通过 `genshin.uid()` 获取当前游戏 UID。
2. 将 `uid` 和 `type` 作为查询参数请求Configuration的 API。
3. 从返回结果中取出 `team` 字段作为目标队伍名称。
4. 执行队伍Switch。

请求格式：

```text
GET {bgi_tools_uid_team_api}?uid={uid}&type={type}
Headers:
  {Token名}: {Token值}
```

期望接口返回格式示例：

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "id": "RecordingID",
    "uid": "玩家UID",
    "team": "目标队伍名称",
    "type": "分组类型"
  }
}
```

> Note：如果接口返回的 `code` 不是 `200`，脚本会Recording错误Log并放弃Switch。如果请求本身Defeat（网络Exception / Error、非 200 状态码等），同样会Recording错误信息。

## Switch Party逻辑

1. 根据Configuration的加载模式确定“目标队伍名称”。
2. 如果队伍名称非空，尝试调用 `genshin.switchParty(team)` Switch Party。
3. 若SwitchDefeat，Auto 传送至Statue of The Seven，再次尝试Switch。
4. 若依然Defeat或发生Exception / Error，会弹出错误通知，并返回游戏主界面，避免影响后续操作。

## FAQ

### 1. 为什么提示“Switch PartyDefeat”？

可能原因包括：

- 当前处于联机模式。
- 当前游戏场景不允许Switch Party，例如Combat状态或禁用区域。
- 队伍名称与游戏内实际Configuration不一致。
- Switch冷却时间未结束。

### 2. Token 应该怎么填？

如果 BgiTools 接口要求的鉴权头是：

```text
Authorization: xxxxx
```

则在Settings中填写：

```text
Authorization=xxxxx
```

脚本会以等号分隔，将前半部分作为 Header 名称，后半部分作为 Header 值。

### 3. 接口返回正常但Switch成功后又Defeated？

请检查返回 JSON 中 `team` 字段是否与游戏内队伍名称完全一致，包括空格、大小写和特殊字符。

## Version历史

- **v1.0.0**
    - 首个Version
    - Supports“输入加载”和“bgi_tools加载”两种队伍获取方式
    - Supports队伍SwitchDefeat后传送Statue of The Seven重试
