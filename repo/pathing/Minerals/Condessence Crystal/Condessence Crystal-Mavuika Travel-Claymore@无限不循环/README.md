1.不要设置行走位
2.Combat策略里不要设置Mavuika的Combat策略，驰轮车重击会提前碎矿导致少捡，另外会打乱Mavuika Travel的节奏
3.本脚本为ClaymoreMining，不Recommended带Zhongli，Razor等技能范围Mining的角色
4.Route里的Monsters / Enemies难度都不高，没太大生存压力。
5.下面为携带角色的Recommended：
刚需：Mavuika（其实你Nope也能跑这 items脚本，慢一点罢了）
盾位：Ineffa/Citlali/Layla/Kirara
Other（按优先级Recommended）：Furina/Escoffier/Lauma/Emilie/Neuvillette（不Recommended有水免怪）/
注意：非常不Recommended携带Yelan，Xilonen等使用技能会进行位移的角色，很容易漏矿（Mavuika除外）



萌新不知道怎么删除MavuikaCombat策略的可以用下面这 items：


// Author：Volcano
// 描述：万能Combat策略（新手Recommended）。需要在，调度器→配置组→设置→Combat配置（开启）→自动检测Combat结束（开启）→更快检查结束Combat（开启）→旋转Searching敌人位置（开启）→检查Combat结束的延时（0.1）→按键触发后检查延时（0.35）→盾奶角色优先释放技能（开启，设置你的盾位）→Combat结束后使用Kaedehara Kazuha长E手机Drops（开启）

// 盾（刚需）
Citlali attack,e,wait(0.2),keypress(q),wait(0.2),keypress(q),wait(0.2),keypress(q),attack(0.2)
Ineffa e,attack(0.22),keypress(q),wait(0.1),keypress(q),attack(0.2),keypress(q),attack(0.2)
Zhongli s(0.2), e(hold), wait(0.2), w(0.2),keypress(q),wait(0.2),keypress(q),attack(0.1)
Layla e,wait(0.2), keypress(q),wait(0.2),keypress(q),attack(0.2),keypress(q),attack(0.2)
Kirara e,attack(0.2), keypress(q),attack(0.2),keypress(q),wait(0.2),keypress(q),attack(0.2)
Thoma e,attack(0.22),keypress(q),wait(0.1),keypress(q),attack(0.2),keypress(q),attack(0.2)
Lan Yan e,attack(0.15), click(middle),attack(0.15),click(middle),attack(0.15),click(middle),wait(0.2).dash(0.1),attack(0.2)

// 后台、挂元素、副C、先手
Dehya e,attack(0.2),e
Xiangling e,wait(0.3),keypress(q),attack(0.2),keypress(q),wait(0.2),keypress(q),attack(0.2)
Arlecchino attack,e
Neuvillette attack(0.23),e
Nahida e(hold),click(middle),keypress(q),wait(0.3),keypress(q),attack(0.3),keypress(q),attack(0.2)
Emilie e,attack(0.2), keypress(q),attack(0.2),keypress(q),wait(0.2),keypress(q),attack(0.2)
Skirk attack(0.2),click(middle),keypress(q),wait(0.05),keypress(q),attack(0.05),click(middle),keydown(E),wait(0.22),attack(0.08),click(middle),keyup(E),keypress(q),wait(0.08),keypress(q)
Furina e,attack(0.2), keypress(q),attack(0.2),keypress(q),wait(0.2),keypress(q),attack(0.2)
Baizhu e,attack(0.2)
Barbara e,attack(0.2)
Sigewinne e(hold),wait(0.2),keypress(q),wait(0.2),keypress(q)
Escoffier e,attack(0.2), keypress(q),attack(0.2),keypress(q),wait(0.2),keypress(q),attack(0.2)
Fischl e
Ororon e,attack(0.3), keypress(q),wait(0.2),attack(0.3),keypress(q),wait(0.2),attack(0.3),keypress(q),wait(0.3)
Raiden Shogun e,attack(0.22),keypress(q),wait(0.1),keypress(q),attack(0.2),keypress(q),attack(0.2)
Kuki Shinobu e,wait(0.2),keypress(q),attack(0.15),keypress(q),e
Varesa e, attack(1.25),wait(0.45), s(0.4), click(middle), e, attack(1.25), wait(0.3),keypress(q), wait(0.45)


// 中置位
Chevreuse attack(0.08),keypress(q),wait(0.2),keypress(q),wait(0.2),attack(0.2),keydown(e),wait(0.15), moveby(0,900),wait(0.15),keyup(e),attack(0.15)
Baizhu attack(0.2), keypress(q),attack(0.2),keypress(q),wait(0.2),keypress(q),attack(0.2)
Neuvillette attack(0.08),keypress(q),wait(0.22),keypress(q),wait(0.2),keypress(q),e


//减抗
Xilonen s(0.2),e,w(0.2),attack(0.35),wait(0.1),attack(0.35),keypress(x), wait(0.2), keypress(q), wait(0.3), keypress(q),keypress(x), wait(0.08), keypress(x),attack(0.2)
Kaedehara Kazuha attack(0.08),keypress(q),wait(0.3),keypress(q),wait(0.3),attack(0.2),keydown(E),wait(0.48),keyup(E),attack(0.3), wait(0.5),attack(0.1)
Sucrose e,attack(0.2),keypress(q),attack(0.2),keypress(q),e,attack(0.2)

//Cleanup，长轴
Neuvillette charge(3),j,wait(0.3)
Skirk attack(0.05),keypress(e),wait(0.05),keypress(e),wait(0.2),attack(2.27),keypress(Q),dash,attack(2.27),keydown(S),keypress(Q),dash,keyup(S),attack(2.27),wait(0.11),charge(0.3),attack(1)
Dehya keypress(q),attack(0.1),dash(0.2),keypress(q),attack(0.3),keypress(q),attack(0.3),keypress(q),attack(0.3),keydown(S),attack(0.5),keyup(S),keydown(W),attack(0.5),keyup(W),keydown(S),attack(0.5),keyup(S),keydown(W),attack(0.5),keyup(W),keydown(S),attack(0.5),keyup(S),keydown(W),attack(0.5),keyup(W),keydown(S),attack(0.5),keyup(S)
Navia keypress(q),attack(0.1),keypress(q),attack(0.1),keypress(q),attack(0.1),keypress(q),keydown(E),wait(0.8),keyup(E),attack(1.6),keydown(E),wait(0.8),keyup(E),attack(0.1),keydown(S),attack(0.33),keyup(S),keydown(W),attack(0.3),keyup(W),keydown(S),attack(0.3),keyup(S),keydown(W),attack(0.3),keyup(W),keydown(S),attack(0.3),keyup(S),keydown(W),attack(0.3),keyup(W),attack(0.2)
Varesa e, attack(1.25),wait(0.45), s(0.4), e, attack(1.25), wait(0.3),keypress(q), wait(0.45),s(0.4),e, attack(1.25),wait(0.45), s(0.4), e, attack(1.25), wait(0.3),keypress(q), attack(0.45)
Arlecchino charge(0.35),j,attack(3.2),j,attack(0.3),attack(0.52),keypress(q),attack(0.2)


2025/9/24/
A02 修 items矿点
A08 优化2条Mavuika Travel，修 items矿点
A17 修2 items矿点
A18 修 items矿点
A19 修2 items矿点
A23 修2 items矿点
A27 去High Risk(有炸药桶)矿点前先开盾，减少暴毙可能
A29 第一 itemsCombat点位易超时，加入角色先开e提前清Common Mobs。修了一段Mavuika Travel
A33 优化Mavuika Travel，适配无Mavuika队伍，修复易卡死移动点位和矿位
A34 修 items矿点
B04 修2 items矿点
B05 大改，删除Mavuika Travel改用嵴峰龙Gogogo!
B06 大改，删除Mavuika Travel改用嵴峰龙Gogogo!
B07 小改一下，防止被怪打死
B09 修 items矿点
B10 修 items矿点
B24 修 items矿点
B28 修 items矿点
B31 修 items矿点，试图避免触发Combat
B35 修正Combat点位
B37 修了Mavuika Travel，防止下车Defeat
B39 修 items矿点