UnderwaterRoute整体效率较慢，怪均较高，仅当Common Mobs权重较高时才会入选
UnderwaterRoute需要单独分组Configuration，使用单独的配队和Combat策略
建议Combat超时时间60秒以上，关闭旋转找怪，Combat策略如下（以Dehya为例，可换为Other抗揍的Character）
Dehya attack,wait(0.1),keypress(e),attack,wait(0.6),attack,wait(0.7),attack
队伍中NopeFurina时需要延长等待时间
Dehya attack,wait(0.1),keypress(e),attack,wait(0.8),attack,wait(0.9),attack

确Approval以使用时，将该部分Route复制到pathing文件夹下任意位置

