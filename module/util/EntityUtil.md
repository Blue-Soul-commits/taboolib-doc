# EntityUtil

## 基本信息
- 类名和包路径: taboolib.platform.util.EntityUtil
- 基本用途: 提供对Bukkit实体的扩展功能
- 类型: Kotlin扩展函数和类
- 所属模块: bukkit-util

## 类结构

### 公开静态方法
> kill(): Unit -> 使生物死亡，将生命值设为0
> getEquipment(slot: BukkitEquipment): ItemStack? -> 获取生物装备
> setEquipment(slot: BukkitEquipment, item: ItemStack): Unit -> 修改生物装备
> safely(): SafeEntity<T> -> 将实体转换为安全实体类

### 公开静态属性
> Entity.groundBlock: Block -> 获取生物脚下的方块
> Entity.groundBlockType: Material -> 获取生物脚下方块的材质

### 内部类
> SafeEntity<T : Entity> -> 安全实体类，处理实体可能失效的情况

### 类方法
> SafeEntity.get(): T -> 获取实体，如果是玩家且失效则尝试重新获取
> SafeEntity.getOrNull(): T? -> 获取实体，如果实体失效则返回null
> SafeEntity.isValid(): Boolean -> 检查实体是否有效

## 实现细节
- 使用Kotlin扩展函数为Bukkit实体类提供额外功能
- SafeEntity类处理实体引用可能失效的情况，特别是针对玩家实体
- 通过Bukkit.getPlayerExact方法重新获取可能失效的玩家实体

## 使用场景
> 需要安全操作可能会失效的实体引用时
> 需要获取实体脚下方块信息时
> 需要快速操作实体装备时
> 需要使生物死亡时

## 注意事项
> SafeEntity类主要解决玩家实体可能失效的问题，对于其他类型的实体不会尝试重新获取
> 使用groundBlock属性时会轻微修改实体位置(add(0.0, -0.01, 0.0))以获取脚下方块

