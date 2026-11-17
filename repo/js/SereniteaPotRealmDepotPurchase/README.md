# README
1. 用于每周一Serenitea Pot洞天百宝购买，可自定义Configuration购买须臾树脂，Hero's Wit，Wanderer's Advice，Mystic Enhancement Ore，Mora，祝圣精华，祝圣油膏
2. 请于阿园附近（显示有对话交互）Starting Up脚本
3. 由于自定义Configuration表单7个之后不显示，所以Fabric的Configuration为空，无法购买
4. 后面可能会添加摆设，摆设图纸，洞天珍物，洞天种物，木材的购买
5. 默认购买最大数量，暂时不Supports自定义数量购买

# Changelog
## 1.1
###  新增了脚本执行星期控制
- 该脚本只在星期一运行，也Supports自定义，例如你希望脚本在周二，周五，周日运行，那么：
1.打开脚本文件夹，用记事本打开main.js文件
2.将代码里的` ALLOWED_DAYS  = [1]; `替换为`ALLOWED_DAYS  = [2,5,7];`
3.保存退出即可
