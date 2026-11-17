# 1. JS脚本的关键Configuration和Path选择

 - **Note:**
	1. 只有严格按照以下步骤Configuration后才能使用，否则将**无法运行**（也可以参考Bottom-Left角的Log来确认下一步需要如何Configuration）
	
	1. 选用的Path需要Happy以下基本要求：Path可靠性强（避免卡死、高难敌人）

 - **Configuration步骤:** 
	
	未Configuration的情况下直接运行Bottom-Left角Log会显示```请在assets/pathing文件夹手动添加Path文件夹后重新运行...```，代表你需要进行如下Configuration
	
	1. 将你的Path文件夹(该文件夹内尤其仅有.json后缀的Path文件)复制粘贴到```assets/pathing```Path
	
	2. 确保原神Top-Left角有派蒙图像，在**调度器**直接运行脚本，Bottom-Left角Log出现```JS脚本Configuration已更新，请重新选择Path...```字样代表JS脚本已经加载了上一步中的Path文件夹，此时脚本应该已经**结束运行**
	
	3. 在**调度器**右键脚本，点击**修改JS脚本自定义Configuration**选择你要执行的Path-Configuration好所有的JSConfiguration（Configuration项**PathSettings-选择要执行的Path文件夹**就It's You刚放入的Path文件加名称）
	
	4. 该步骤根据你选择的加世界模式有所区别
	
		1. 手动加世界
	 
			确保在**多人模式**下，运行脚本，此时脚本会在聊天框发送校验信息，代表脚本正常运行
		
		2. Auto 加世界
		
			确保在**单人模式**下，运行脚本，此时脚本会Auto 等待队员加入(作为领队)或加入队长世界(作为队员)，代表脚本正常运行
	
		

 - **更多的Path：**
	
	如果需要添加更多的Path文件，请重复以上**Configuration步骤**的```1-4```添加Path文件夹即可(文件夹名称不可重复)
	
	添加完成后在**JS脚本自定义Configuration**的**请选择要执行的Path文件夹**下拉菜单选择对应的Path

# 2. JS脚本自定义ConfigurationGuide / Instructions

 - **选择加入世界的方式**
 
	1. Auto 加世界 \[Recommended\]
		
		选择这个选项后，需要Configuration下方的```Auto 加世界```内的三个Configuration项
	
	2. 手动加世界
	
		选择这个选项后，需要Configuration下方的```Auto 加世界```内的两个个Configuration项

 - **手动加世界-请挑选你的玩家标识:**
 
	手动加世界模式下，在所有人都已经加入世界的情况下，你的玩家标识

 - **手动加世界-选择玩家总数:**
 
	手动加世界模式下，在所有人都已经加入世界的情况下的玩家总数

 - **Auto 加世界-请挑选你的身份:**
 
	Auto 加世界模式下，你作为领队还是队员（领队只能存在一个，选择多个可能会报错）

 - **Auto 加世界-文本输入框**
 
	1. 作为领队
	
		填入要加入你世界的所有玩家的昵称（顺序无关），每个玩家的名称ID使用单个空格隔开
	
	2. 作为队员
	
		填入你要加入的世界（队长）的UID
	
 - **Auto 加世界-名称匹配模式:**
 
	Auto 加世界模式下，匹配玩家名称的匹配方式（仅队长生效）
	
	1. 全字匹配（此模式下请使用玩家的全称）
	
		匹配玩家的完整名称，在玩家的名称便于识别时使用
	
	2. 部分匹配（此模式下请填入玩家名称内易于识别的**连续文本**）
	
		匹配玩家名称内包含的文本，在玩家的名称难以识别时使用
 
 - **PathSettings-选择要执行的Path文件夹**
 
	初次使用时该下拉菜单为空，详情Configuration见下方```2. JS脚本的关键Configuration和Path选择```

# 3. Precautions / Notes

	所有人使用的Path文件夹及其内容应当**完全一致**，否则验证Defeat会导致脚本Exception / Error终止

 - **Path文件夹存放位置:** ```assets/pathing```

	假设你有一个文件夹名为```死亡笔记-400```，这个文件夹内含有若干个```.json```后缀的Path文件，你需要将```死亡笔记-400```文件夹复制粘贴到```assets/pathing```文件夹内
	
 - **Path相关格式:** ```assets/pathing/你的Path文件夹名/若干Path文件.json...```
 
	Path```assets/pathing```内只能存放文件夹，存放Other文件无效
	
	Path```assets/pathing你的Path文件夹名```内只能存放```.json```后缀的文件

 - **assets/pathing文件夹下已经内置了部分Path**
	
	内置的Path已经做过联机情况下的适配，可以Relaxed使用

# 4.适用场景

 - **同步运行同一组Path追踪文件**
 
	自行探索，理论上所有地图追踪文件都可以同步执行

 - **Configuration了本地远程，可以在一个设备上运行两套原神+BGI：**
 
	可以用两个Account实现双倍的锄地收益，例如在调度器内都Configuration两个锄地脚本，一个先作为房主后作为成员，另一个先作为成员后作为房主，可以Auto 实现两个号同时锄地，锄完两个世界的资源
	
 - **和OtherBGI用户一起锄地：**
 
	所有人协商好，正确导入相同的Path后就可以实现2-4人的联机锄地（Route进度将保持同步，确保所有玩家都能获得相同的收益）
