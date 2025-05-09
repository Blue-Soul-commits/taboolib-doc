# BukkitLocation
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitLocation
- 基本用途: 提供Bukkit平台与TabooLib通用位置对象之间的转换函数
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构
### 公开静态方法
> taboolib.common.util.Location.toBukkitLocation(): org.bukkit.Location -> 将TabooLib通用位置对象转换为Bukkit位置对象
> org.bukkit.Location.toProxyLocation(): taboolib.common.util.Location -> 将Bukkit位置对象转换为TabooLib通用位置对象

## 实现细节
- toBukkitLocation()函数将TabooLib的Location对象转换为Bukkit的Location对象
- 使用world字符串获取对应的Bukkit世界对象，如果world为null则世界也为null
- toProxyLocation()函数将Bukkit的Location对象转换为TabooLib的Location对象
- 保留了位置的所有属性：x、y、z坐标以及yaw、pitch旋转角度

## 使用场景
> 在跨平台代码和Bukkit特定代码之间传递位置信息
> 将TabooLib通用API返回的位置转换为Bukkit可用的位置对象
> 将Bukkit事件或API提供的位置转换为可在TabooLib通用代码中使用的格式
> 在需要持久化存储位置信息时，转换为通用格式后再序列化

## 注意事项
> 世界名称在转换过程中可能会丢失，如果原始世界不存在或已卸载
> Bukkit.getWorld(name)可能返回null，使用时应注意空值检查
> 这些函数是平台适配层的一部分，通常不需要直接调用，而是通过TabooLib的平台API使用
> 在多平台插件中，应优先使用taboolib.common.platform.function.adaptLocation和platformLocation函数
