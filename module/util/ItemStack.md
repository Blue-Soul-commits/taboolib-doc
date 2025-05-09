# ItemStack

## 基本信息
- 类名和包路径: taboolib.platform.util.ItemStack
- 基本用途: 提供Bukkit物品栈的扩展属性，用于快速判断物品是否为空气
- 类型: Kotlin扩展属性文件
- 所属模块: bukkit-util

## 类结构

### 公开静态属性
> XMaterial.isAir: Boolean -> 判定XMaterial材质是否为空气
> ItemStack?.isAir: Boolean -> 判定ItemStack物品是否为空气

## 实现细节
- 为XMaterial类添加isAir扩展属性，检查是否为AIR、CAVE_AIR或VOID_AIR
- 为ItemStack类添加isAir扩展属性，通过调用isAir()函数实现
- 使用Kotlin的可空类型(ItemStack?)确保对空引用的安全处理
- 使用Kotlin的扩展属性语法提供简洁的API

## 使用场景
> 需要快速判断物品是否为空气时
> 处理物品栏内容时需要过滤空气物品
> 使用XMaterial跨版本兼容系统时需要判断材质
> 开发物品相关功能时需要空检查
> 实现物品过滤或计数功能时

## 注意事项
> isAir属性是只读的，不能被修改
> ItemStack?.isAir属性实际上调用的是isAir()函数，该函数在ItemModifier.kt中定义
> 该扩展属性与Bukkit原生的Material.isAir()方法功能类似，但支持XMaterial和可空类型
> 在处理物品时，应优先使用这些扩展属性进行空气检查，以提高代码可读性

