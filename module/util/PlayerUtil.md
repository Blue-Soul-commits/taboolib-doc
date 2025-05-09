# PlayerUtil

## 基本信息
- 类名和包路径: taboolib.platform.util.PlayerUtil
- 基本用途: 提供Bukkit玩家(HumanEntity)相关的实用扩展函数，简化常见操作
- 类型: Kotlin扩展函数文件
- 所属模块: bukkit-util

## 类结构

### 公开静态方法
> HumanEntity.getEmptySlot(hasEquipment: Boolean = false, isItemAmount: Boolean = false): Int -> 获取玩家背包中的空槽位数量
> HumanEntity.giveItem(itemStack: List<ItemStack>): Unit -> 给予玩家多个物品
> HumanEntity.giveItem(itemStack: ItemStack?, repeat: Int = 1): Unit -> 给予玩家物品，可指定重复次数
> HumanEntity.getUsingItem(material: Material): ItemStack? -> 获取玩家正在使用的指定材质的物品
> HumanEntity.sendActionBar(message: String): Unit -> 向玩家发送动作栏消息
> HumanEntity.actionBar(message: String): Unit -> 向玩家发送动作栏消息（别名）
> HumanEntity.title(title: String?, subTitle: String?): Unit -> 向玩家发送标题和副标题，使用默认的淡入淡出时间
> HumanEntity.title(title: String?, subTitle: String?, fadeIn: Int, stay: Int, fadeOut: Int): Unit -> 向玩家发送标题和副标题，可自定义淡入淡出时间
> HumanEntity.feed(): Unit -> 将玩家的饥饿值恢复到最大值（20）
> HumanEntity.saturate(): Unit -> 将玩家的饱和度恢复到最大值（20.0）

## 实现细节
- 使用Kotlin扩展函数为HumanEntity类提供额外功能
- 通过adaptPlayer函数将Bukkit玩家对象转换为跨平台的ProxyPlayer对象
- getEmptySlot函数通过遍历物品栏内容计算空槽位数量
- giveItem函数在给予物品前保存原始数量，防止物品数量在添加过程中被修改
- 物品无法放入背包时会自动掉落在玩家位置
- 提供了多个UI相关函数(actionBar, title)简化消息显示

## 使用场景
> 需要检查玩家背包空间时
> 安全地给予玩家物品时
> 检测玩家手持特定物品时
> 向玩家发送UI元素(标题、动作栏)时
> 恢复玩家饥饿值和饱和度时

## 注意事项
> getEmptySlot的hasEquipment参数为true时会减去装备栏的空槽位
> giveItem函数会自动处理物品溢出，将无法放入背包的物品掉落在地上
> giveItem函数会保护原始物品的数量不被修改
> 使用getUsingItem时，只会检查主手和副手，不会检查装备栏
> 使用title函数时，时间单位为tick(1秒=20tick)

