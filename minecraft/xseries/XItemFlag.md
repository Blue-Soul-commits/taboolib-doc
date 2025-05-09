# XItemFlag

## 基本信息
- 类名和包路径: taboolib.library.xseries.XItemFlag
- 基本用途: 提供跨版本的 Minecraft 物品标志枚举，解决不同版本 ItemFlag 命名差异问题
- 类型: 枚举类
- 所属模块: platform-bukkit-impl (TabooLib XSeries 库)

## 类结构

### 公开静态字段
> REGISTRY: XRegistry<XItemFlag, ItemFlag> -> 物品标志注册表，用于管理 XItemFlag 与 Bukkit ItemFlag 的映射关系
> BUKKIT_VALUES: ItemFlag[] -> 所有 Bukkit ItemFlag 值的数组
> HIDE_ADDITIONAL_TOOLTIP: XItemFlag -> 隐藏药水效果、书籍和烟花信息、地图提示、旗帜图案等
> HIDE_ARMOR_TRIM: XItemFlag -> 隐藏盔甲纹饰名称
> HIDE_ATTRIBUTES: XItemFlag -> 隐藏物品属性
> HIDE_DESTROYS: XItemFlag -> 隐藏物品可破坏的方块信息
> HIDE_DYE: XItemFlag -> 隐藏染色皮革盔甲的染料名称
> HIDE_ENCHANTS: XItemFlag -> 隐藏物品附魔
> HIDE_PLACED_ON: XItemFlag -> 隐藏物品可放置的方块信息
> HIDE_STORED_ENCHANTS: XItemFlag -> 隐藏存储的附魔（如附魔书上的附魔）
> HIDE_UNBREAKABLE: XItemFlag -> 隐藏物品的不可破坏属性文本

### 公开静态方法
> of(itemFlag: ItemFlag): XItemFlag -> 根据 Bukkit ItemFlag 获取对应的 XItemFlag
> of(itemFlag: String): Optional<XItemFlag> -> 根据物品标志名称获取对应的 XItemFlag，返回 Optional
> getValues(): Collection<XItemFlag> -> 获取所有可用的 XItemFlag 值
> hideEverything(meta: ItemMeta): void -> 向物品元数据添加所有物品标志，隐藏所有附加信息

### 类内可被访问字段
> itemFlag: ItemFlag -> 当前 XItemFlag 对应的 Bukkit ItemFlag

### 类方法
> friendlyName(): String -> 获取物品标志的友好名称
> isSupported(): boolean -> 检查当前服务器版本是否支持此物品标志
> or(other: XItemFlag): XItemFlag -> 如果当前物品标志不受支持，则返回替代物品标志
> getNames(): String[] -> 获取物品标志的所有可能名称
> get(): ItemFlag -> 获取对应的 Bukkit ItemFlag
> set(item: ItemStack): void -> 向物品添加此物品标志
> set(meta: ItemMeta): void -> 向物品元数据添加此物品标志
> removeFrom(item: ItemStack): void -> 从物品移除此物品标志
> removeFrom(meta: ItemMeta): void -> 从物品元数据移除此物品标志
> getFlags(item: ItemStack): Set<XItemFlag> -> 获取物品上的所有物品标志
> getFlags(meta: ItemMeta): Set<XItemFlag> -> 获取物品元数据上的所有物品标志
> has(item: ItemStack): boolean -> 检查物品是否有此物品标志
> has(meta: ItemMeta): boolean -> 检查物品元数据是否有此物品标志

## 实现细节
- 使用 XRegistry 系统管理不同版本的物品标志映射
- 通过构造函数中的别名参数支持不同版本的物品标志名称
- 使用 @XChange 和 @XInfo 注解标记版本变更和物品标志信息
- 内部使用 Data 静态类初始化注册表，避免循环依赖
- HIDE_STORED_ENCHANTS 在 1.21.3 版本中从 HIDE_ADDITIONAL_TOOLTIP 功能中分离出来

## 使用场景
> 需要在不同 Minecraft 版本间兼容物品标志时使用
> 当需要通过字符串名称获取物品标志时使用
> 在创建装饰性物品时，隐藏所有附加信息
> 在物品构建器中设置物品标志

## 注意事项
> 某些物品标志在特定版本中可能不存在，使用前应检查 isSupported() 方法
> 使用 @XChange 注解标记的物品标志表示在特定版本中发生了命名变更
> HIDE_ADDITIONAL_TOOLTIP 在 1.21 版本从 HIDE_POTION_EFFECTS 更名
> 使用 hideEverything() 方法可以一次性隐藏所有物品信息，适用于装饰性物品

