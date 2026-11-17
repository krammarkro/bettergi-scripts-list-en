请Note本脚本采用的方法是，刷取物品至指定数量，如果Nope刷取完成，中途请不要使用！！！

再说一遍，Nope刷取完成，中途请不要使用！！！

当物品刷取完成之后会跳过执行，刷取过程中出现问题也会通知，所以强烈建议打开JS消息通知。

目前只刷取Character突破素材、天赋书、技能培养素材，武器材料，不会升级以及合成(区域特产、怪物掉落物，不考虑添加，咕咕……)，建议额外在All-in-One Run中添加Auto Domain刷取Artifacts和每日领奖兜底。

脚本的基本运行逻辑是，解析培养方案后，优先查看体力，体力充足的情况下，检查物品数量，物品不够，将会Go to对应的Domain刷取(考虑了合成时额外产出的情况，实际物品可能会少一些)，DomainNope开启，检测后会跳过，当材料刷满后会发送通知，并且Recording本次刷取的数据, 为避免重复刷取，相同数值会并认定为填写错误，可以勾选Settings里的清空Recording解决。

Usage：打开米游社找到养成计算器，选择需要培养的Character，确认好培养方案后，查看总共需要多少材料(Note不是还需要多少材料!!!)，依次填入即可，不知道 boss 叫什么名字的，点击计算器里的 boss 掉落物物图标即可Go to查看。

假设需要自由天赋书，绿色的三本，蓝色的五本，紫色的一本，输入方式为"3-5-1",假设需要武器材料雾海云间，绿色的零个，蓝色的5个、紫色的11个，金色的6个输入方式为"0-5-11-6"，自定义Settings提供了三个常见的挡位参考。

Configuration组SettingsPrecautions / Notes 1、开启地图追踪行走Configuration 2、关闭Auto 拾取 3、开启CombatConfiguration 4、Combat策略选择"根据队伍Auto 选择"（有万能策略请自行测试效果） 5、关闭Auto 拾取 6、Other默认就行，练度较低的话，Combat超时时间可以加长

OtherConfiguration需要Note的有，Domain刷取调用的是独立任务中的Configuration，请在独立任务中的Auto Domain选择Combat的队伍，但请不要选择任何Domain，要刷Artifacts请选择All-in-One Run中的Auto DomainConfiguration。

由于地图TemplateMatch技术失传，BOSSSuper-Heavy Landrover: Mechanized Fortress、Immortal Construct，Go to过程采用了键鼠脚本的方式，键鼠脚本使用Zhongli作为一号位，队伍Nope任何移速加成， 如果无法正常前请自行录制键鼠脚本，并替换assets/goToBoss文件夹中对应指定的文件。

未来计划（取消重复数值刷取Protection，改为刷取完成后，将材料名称改为"无"，同时Supports更加简洁地输入材料数量，比如输入888，代表刷取三个等级1到等级8的技能书材料）




