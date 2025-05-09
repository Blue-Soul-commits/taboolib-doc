# MetaHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.handler.MetaHandler
- 基本用途: 用于检查实体是否拥有特定元数据标签
- 类型: 实现EntityHandler接口的具体处理器类
- 所属模块: 实体匹配工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> check(entity: LivingEntity, value: String): Boolean -> 检查Bukkit生物实体是否拥有指定的元数据标签
> check(entity: BaseEntityInstance, value: String): Boolean -> 检查自定义实体实例是否拥有指定的标签
> condition(value: String): String? -> 解析条件字符串，提取元数据/标签键名

## 实现细节
- 实现了EntityHandler接口，专门用于处理实体元数据/标签匹配逻辑
- 对于Bukkit的LivingEntity，使用taboolib提供的hasMeta方法检查元数据
- 对于自定义的BaseEntityInstance，使用其hasTag方法检查标签
- 使用ParserUtils工具类从物品匹配模块解析字符串条件

## 使用场景
> 在需要根据元数据标签筛选实体时使用，例如找出带有特定标记的实体
> 在配置文件中定义基于元数据/标签的实体匹配条件时，通过该处理器解析并执行匹配

## 注意事项
> 对于LivingEntity和BaseEntityInstance使用不同的检查方法：前者检查meta，后者检查tag
> 如果condition方法无法从条件中提取有效键名（返回null），两种check方法都会返回false
> 使用的ParserUtils来自item匹配模块(top.maplex.arim.tools.itemmatch.util)，而不是实体匹配模块
