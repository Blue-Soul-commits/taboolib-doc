# SourceMinecraft

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceMinecraft
- 基本用途: Minecraft原生物品的ItemSource接口实现，用于获取原版物品和玩家装备
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"minecraft"
> alias: List<String> -> 物品库别名列表，包含"mc"、"eq"、"equip"
> pluginName: String -> 物品库对应的插件名称，值为"Minecraft"
> isLoaded: Boolean -> 物品库是否已加载，固定返回true（原版Minecraft总是可用）

### 类方法
> build(id: String, player: Player?): ItemStack -> 根据ID构建Minecraft物品或获取玩家装备

## 实现细节
- 实现了ItemSource接口，提供获取Minecraft原版物品和玩家装备的能力
- 重写了isLoaded属性，固定返回true，因为Minecraft是服务器的基础部分
- 支持两种主要的物品获取方式：
  1. 装备获取：当ID以"eq"或"equip"开头，获取玩家指定槽位的装备
  2. 物品获取：通过物品名称获取对应的Minecraft原版物品
- 在物品名称匹配中，支持三级匹配策略：
  1. 精确匹配当前版本物品名称
  2. 匹配旧版本遗留物品名称
  3. 使用字符串相似度查找最相似的物品
- 使用XMaterial类处理跨版本物品兼容性
- 当所有匹配都失败时，尝试直接通过大写ID获取Material，如果仍失败可能会抛出异常

## 使用场景
> 在物品管理系统中提供对原版Minecraft物品的访问
> 获取玩家当前装备的物品，例如复制玩家手持物品
> 在没有其他物品源提供对应功能时作为基础物品获取手段
> 在配置文件中通过简单的ID引用原版物品

## 注意事项
> 使用装备获取功能需要提供有效的player参数，否则可能返回空气或null
> 当使用不存在的Material名称且没有相似匹配时，可能会抛出IllegalArgumentException异常
> 没有使用warnItemNotFound方法报告错误，而是通过多级匹配尝试找到最相似的物品
> 使用字符串相似度匹配可能会返回意外的结果，需谨慎使用
> 与其他物品源不同，此实现在找不到物品时可能会返回空气(Material.AIR)而非基岩
