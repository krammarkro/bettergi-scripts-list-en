# 千星奇域-猜Character辅助

## Instructions

- 脚本需要在奇域内启动。
- 退出奇域后记得关闭脚本。
- 自定义Settings中有OtherFeatures，可根据需要进行开关。
- 3.0VersionStarting Up携带完整台词数据。

## 数据维护

- 在线表格：https://docs.qq.com/sheet/DVlF4V1RhRXlQakZk
- 每类台词只占一列，单元格内一行一条台词。
- 导出 CSV 时使用文件名 `千星奇域-猜Character辅助-Working表1.csv`。
- 导出 CSV 后运行：

```bash
node csv_to_json.js
```

## 数据结构

CSV/Excel 使用紧凑列，例如 `元素战技台词`、`元素爆发台词`、`入队语音`。同一类里的多条内容放在同一个单元格内，每行一条。

生成 `data.json` 时会Auto 归并为数组结构：

```json
{
  "Character名": "Amber",
  "信息": {
    "Character名": "Amber",
    "性别": "女"
  },
  "台词": {
    "元素战技": ["靠你咯。", "兔兔伯爵，出击！"]
  },
  "命之座": ["一箭双丘丘!"],
  "天赋": ["Marksmanship"]
}
```
