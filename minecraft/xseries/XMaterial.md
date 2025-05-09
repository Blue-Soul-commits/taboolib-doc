# XMaterial
## 基本信息
- 类名和包路径: taboolib.library.xseries.XMaterial
- 基本用途: 提供跨版本的Minecraft材质支持，解决不同Minecraft版本中材质名称和数据值变化的问题
- 类型: 枚举类
- 所属模块: taboolib.library.xseries

## 类结构
### 公开静态字段
> VALUES: XMaterial[] -> 缓存的XMaterial.values()数组，避免重复调用values()方法分配内存
> MAX_DATA_VALUE: byte -> 预扁平化更新中的最大数据值，属于VILLAGER_SPAWN_EGG (120)
> UNKNOWN_DATA_VALUE: byte -> 用于表示传递对象(名称或材质)的数据值未提供或无效 (-1)
> MAX_ID: short -> 预扁平化更新前的最大材质ID，属于MUSIC_DISC_WAIT (2267)

### 公开静态方法
> getVersion(): int -> 获取当前服务器版本号
> supports(version: int): boolean -> 检查指定版本是否等于或低于当前服务器版本
> matchXMaterial(name: String): Optional<XMaterial> -> 将给定的材质名称解析为XMaterial
> matchXMaterial(material: Material): XMaterial -> 将给定的Material解析为XMaterial
> matchXMaterial(item: ItemStack): XMaterial -> 将给定的ItemStack解析为XMaterial
> matchDefinedXMaterial(name: String, data: byte): Optional<XMaterial> -> 将给定的材质名称和数据值解析为XMaterial
> format(name: String): String -> 将材质名称格式化为枚举名称格式

### 类内可被访问字段
> data: byte -> 材质的数据值（预扁平化）
> legacy: String[] -> 旧版本中使用的材质名称列表
> material: Material -> 缓存的Bukkit解析材质

### 类方法
> getLegacy(): String[] -> 获取旧版本中使用的材质名称列表
> setType(item: ItemStack): ItemStack -> 设置物品的Material（在旧版本上还会设置数据值）
> anyMatchLegacy(name: String): boolean -> 检查给定的材质名称是否匹配此XMaterial的任何旧版材质名称
> toString(): String -> 将枚举名称解析为用户友好的名称
> getId(): int -> 获取材质的ID（魔法值）
> getData(): byte -> 获取材质的数据值（预扁平化）
> parseItem(): ItemStack -> 从此XMaterial解析物品，在旧版本上使用数据值
> parseMaterial(): Material -> 解析此XMaterial的材质（已弃用，使用get()代替）
> isSimilar(item: ItemStack): boolean -> 检查物品是否具有相同的材质（在旧版本上还会检查数据值）
> get(): Material -> 获取与此XMaterial关联的Bukkit Material
> isDuplicated(): boolean -> 检查材质是否有任何重复项

## 实现细节
- 使用枚举实现，包含所有Minecraft材质，包括1.8到最新版本的所有材质
- 通过缓存和映射优化性能，避免重复解析材质名称
- 使用数据值处理1.13版本前的材质差异（预扁平化）
- 处理特殊情况如SPLASH_POTION，它在预扁平化版本中不是官方材质
- 解决"XMaterial悖论"，处理1.13前后版本中重复的材质名称
- 通过反射获取Material.BY_NAME字段，解决Paper在1.21.3+版本中Material.getMaterial()行为异常的问题

## 使用场景
> 创建跨版本兼容的物品，无需担心不同Minecraft版本的材质名称变化
> 解析配置文件中的材质名称，支持旧格式（如"WOOL:14"）和新格式（如"RED_WOOL"）
> 检查物品的材质类型，无需编写版本特定的代码
> 在插件中使用最新的材质名称，同时保持对旧版本的兼容性

## 注意事项
> 在1.13之前的版本中，某些材质有数据值，需要特别处理
> 某些材质在不同版本中有不同的名称，如GREEN_DYE在1.13中为CACTUS_GREEN
> 地图物品(MAP/FILLED_MAP)需要特殊处理，因为它们的数据值有特殊用途
> 在处理可损坏的物品（如工具、武器）时，不应使用数据值来区分材质
> 某些方法（如parseMaterial()）已被弃用，应使用新方法（如get()）

