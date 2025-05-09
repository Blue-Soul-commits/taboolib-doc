# AdyHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.handler.AdyHandler
- 基本用途: 用于实体ID匹配检查的处理器
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
> check(entity: LivingEntity, value: String): Boolean -> 检查Bukkit生物实体是否匹配给定条件字符串，此实现始终返回false
> check(entity: BaseEntityInstance, value: String): Boolean -> 检查自定义实体实例是否匹配给定条件字符串
> checkEntity(entityID: String, value: String): Boolean -> (私有方法) 根据条件检查实体ID
> checkStringCondition(string: String, condition: MatchCondition.StringCondition): Boolean -> (私有方法) 根据字符串条件检查实体ID

## 实现细节
- 实现了EntityHandler接口，专门用于处理实体ID匹配逻辑
- 支持复合条件检查，包括ANY（任一匹配）、ALL（全部匹配）和NONE（无一匹配）
- 支持多种字符串操作类型：精确匹配、包含、正则表达式、开头匹配和结尾匹配
- 支持条件修饰符，如lowercase或lc用于将字符串转为小写再进行比较
- 字符串比较默认忽略大小写

## 使用场景
> 在需要根据ID匹配实体时，例如筛选特定类型的实体
> 在配置文件中定义复杂的实体匹配条件时，通过该处理器解析并执行匹配

## 注意事项
> 对于原生LivingEntity实体，check方法总是返回false，实际功能仅针对BaseEntityInstance接口的实现
> 使用时需要确保传入的value字符串符合可解析的条件格式，否则匹配可能失败
> 条件解析依赖ParserUtils工具类
