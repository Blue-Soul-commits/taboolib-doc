# ItemModifier

## 基本信息
- 类名和包路径: taboolib.platform.util.ItemModifier
- 基本用途: 提供物品检测和修改的扩展函数
- 类型: Kotlin扩展函数集合
- 所属模块: bukkit-util

## 类结构

### 公开静态方法
> Material?.isAir(): Boolean -> 检查材质是否为空气
> Material?.isNotAir(): Boolean -> 检查材质是否不为空气
> ItemStack?.isAir(): Boolean -> 检查物品是否为空气
> ItemStack?.isNotAir(): Boolean -> 检查物品是否不为空气
> ItemStack.modifyMeta<T : ItemMeta>(func: T.() -> Unit): ItemStack -> 编辑物品元数据
> ItemMeta.modifyLore(func: MutableList<String>.() -> Unit): ItemMeta -> 编辑物品描述
> ItemStack.modifyLore(func: MutableList<String>.() -> Unit): ItemStack -> 编辑物品描述
> ItemStack.hasName(name: String? = null): Boolean -> 判断物品是否存在名称或特定名称
> ItemStack.hasLore(lore: String? = null): Boolean -> 判断物品是否存在描述或特定描述
> ItemStack.replaceName(nameOld: String, nameNew: String): ItemStack -> 替换物品名称
> ItemStack.replaceLore(loreOld: String, loreNew: String): ItemStack -> 替换物品描述
> ItemStack.replaceName(map: Map<String, String>): ItemStack -> 批量替换物品名称
> ItemStack.replaceLore(map: Map<String, String>): ItemStack -> 批量替换物品描述

## 实现细节
- 使用Kotlin契约(contract)确保空安全，当isAir()返回false时，编译器知道对象不为null
- 使用Kotlin扩展函数为Material和ItemStack类提供额外功能
- 提供流畅的API来修改物品属性
- 支持泛型ItemMeta操作，允许处理特定类型的元数据
- 使用ImmutableMap简化单一替换操作

## 使用场景
> 需要安全检查物品是否为空气时
> 需要修改物品名称或描述时
> 需要批量替换物品文本内容时
> 需要对特定类型的物品元数据进行操作时
> 开发GUI界面或物品系统时

## 注意事项
> 对空气物品调用modifyMeta或modifyLore会抛出"air"错误
> isAir方法会检查物品是否为null、Material.AIR或名称以"_AIR"结尾
> 替换操作只会在物品已有名称或描述时生效
> 使用泛型modifyMeta时需确保物品元数据类型正确，否则操作不会生效
