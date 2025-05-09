# HealthHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.handler.HealthHandler
- 基本用途: 用于检查实体生命值是否符合特定条件
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
> check(entity: LivingEntity, value: String): Boolean -> 检查Bukkit生物实体的生命值是否符合给定条件字符串
> check(entity: BaseEntityInstance, value: String): Boolean -> 检查自定义实体实例的生命值是否符合条件，此实现始终返回false

## 实现细节
- 实现了EntityHandler接口，专门用于处理实体生命值匹配逻辑
- 使用ParserUtils工具类解析数值条件
- 支持多种数值比较操作符：大于等于、小于等于、大于、小于和等于
- 只对原生Bukkit的LivingEntity提供有效实现，对BaseEntityInstance总是返回false

## 使用场景
> 在需要根据生命值筛选实体时使用，例如找出低血量的怪物
> 在配置文件中定义基于生命值的实体匹配条件时，通过该处理器解析并执行匹配

## 注意事项
> 对于自定义BaseEntityInstance实体，check方法总是返回false，实际功能仅针对原生LivingEntity
> 使用时需要确保传入的value字符串符合可解析的数值条件格式，否则匹配可能失败
