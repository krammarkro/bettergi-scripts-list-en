简单介绍：
脚本Supports选择Normal便携Teleport Waypoint或Zibai的Friendship物品「青玄乘阳华盖」。
脚本每六天会重置一次便携Teleport Waypoint的 CD，之后一直连续包月。
首次运行会Auto 续费一次, 另外补充一个小知识，两种Teleport Waypoint只能存其一。

具体Usage：
首先你需要学会录制地图追踪，不会的自己去官网学。
地图追踪文件的第一个点位，It's You需要放置Teleport Waypoint的点位，类型选择传送，动作选择Other里面的强制传送。制作好的地图追踪文件，命名为"续费"放入脚本的assets文件夹中。
此外，强烈建议额外录制一个完整Go to便携Teleport Waypoint的地图追踪文件，当你长期不登录, 或者你临时又放置了一个Teleport Waypoint, 会导致你之前的Teleport Waypoint无法正常续费，录制了这个文件可以用于恢复Teleport Waypoint。文件需要命名为"恢复"，放入脚本的assets文件夹中。
最后制作好的地图追踪文件，录制完成后，一定要测试一下。看恢复文件能否正常Go to指定地方，看续费文件能否正常传送到指定位置。

使用细节：
详细讲一下恢复流程，当需要续费的Teleport Waypoint不存在的时候，首先会经历传送Defeat的情况，这个过程等待的时间会Compare长，大约30s，这是BGI本体的原因，之后如果有用于恢复的地图追踪文件，就会Starting Up正常恢复了。

未来计划：
部分特别的传送地点，BGI本体的地图追踪不Supports，未来会考虑通过键鼠脚本传送，小地图的模板匹配检测传送成功的方案来兼容，此外考虑添加选择续费到指定日期……（咕咕）

