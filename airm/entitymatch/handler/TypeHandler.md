# TypeHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.handler.TypeHandler
- 基本用途: 用于检查实体类型是否符合特定条件
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
> check(entity: LivingEntity, value: String): Boolean -> 检查Bukkit生物实体的类型是否符合给定条件字符串
> check(entity: BaseEntityInstance, value: String): Boolean -> 检查自定义实体实例的类型是否符合给定条件字符串
> condition(entityType: String, value: String): Boolean -> 根据条件字符串检查实体类型是否匹配

## 实现细节
- 实现了EntityHandler接口，专门用于处理实体类型匹配逻辑
- 对于Bukkit的LivingEntity，获取其type.name作为实体类型
- 对于自定义的BaseEntityInstance，获取其entityType.name作为实体类型
- 使用ParserUtils工具类解析字符串条件
- 支持多种字符串操作类型：精确匹配、包含、正则表达式、开头匹配和结尾匹配
- 所有比较都忽略大小写

## 使用场景
> 在需要根据实体类型筛选实体时使用，例如只选择特定种类的怪物
> 在配置文件中定义基于实体类型的匹配条件时，通过该处理器解析并执行匹配

## 注意事项
> 实体类型名称基于Bukkit的EntityType枚举或自定义实体系统的类型名
> 条件匹配不区分大小写，所以"zombie"和"ZOMBIE"被视为相同
> condition方法可以单独使用，直接传入实体类型字符串和条件
