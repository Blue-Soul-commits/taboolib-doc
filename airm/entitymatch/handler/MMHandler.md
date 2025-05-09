# MMHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.handler.MMHandler
- 基本用途: 用于MythicMobs实体的匹配检查
- 类型: 实现EntityHandler接口的具体处理器类
- 所属模块: 实体匹配工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> mythic: Mythic.API -> MythicMobs的API接口对象

### 类方法
> check(entity: LivingEntity, value: String): Boolean -> 检查Bukkit生物实体是否为符合条件的MythicMobs实体
> check(entity: BaseEntityInstance, value: String): Boolean -> 检查自定义实体实例是否匹配条件，此实现始终返回false
> checkEntity(entityID: String, value: String): Boolean -> (私有方法) 根据条件检查MythicMobs实体ID
> checkStringCondition(string: String, condition: MatchCondition.StringCondition): Boolean -> (私有方法) 根据字符串条件检查实体ID

## 实现细节
- 实现了EntityHandler接口，专门用于处理MythicMobs实体匹配逻辑
- 使用MythicMobs的API获取实体的MythicMobs ID
- 支持复合条件检查，包括ANY（任一匹配）、ALL（全部匹配）和NONE（无一匹配）
- 支持多种字符串操作类型：精确匹配、包含、正则表达式、开头匹配和结尾匹配
- 支持条件修饰符，如lowercase或lc用于将字符串转为小写再进行比较
- 与AdyHandler具有相似的字符串条件检查逻辑，但应用于MythicMobs实体

## 使用场景
> 在需要根据MythicMobs实体ID筛选实体时使用
> 在配置文件中定义基于MythicMobs ID的实体匹配条件时，通过该处理器解析并执行匹配
> 与其他插件集成时，需要识别特定类型的MythicMobs怪物

## 注意事项
> 对于非MythicMobs实体或无法获取MythicMobs ID的实体，check方法会返回false
> 对于自定义BaseEntityInstance实体，check方法总是返回false
> 需要服务器安装MythicMobs插件并正确配置，否则无法使用
> 依赖ink.ptms.um.Mythic库进行MythicMobs实体的识别
