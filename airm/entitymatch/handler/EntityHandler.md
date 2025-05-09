# EntityHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.handler.EntityHandler
- 基本用途: 定义实体匹配处理的接口规范
- 类型: 接口(Interface)
- 所属模块: 实体匹配工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> check(entity: LivingEntity, value: String): Boolean -> 检查Bukkit生物实体是否匹配给定条件字符串
> check(entity: BaseEntityInstance, value: String): Boolean -> 检查自定义实体实例是否匹配给定条件字符串

## 实现细节
- 这是一个接口，定义了两个方法签名，用于检查不同类型的实体是否符合特定条件
- 提供了两种实体类型的检查方法：原生Bukkit的LivingEntity和自定义的BaseEntityInstance
- 实现类需要提供具体的匹配逻辑实现

## 使用场景
> 作为实体匹配系统的基础接口，被各种具体匹配处理器实现
> 在需要根据不同条件判断实体是否符合要求的场景中使用

## 注意事项
> 实现此接口的类需要实现所有定义的方法
> 两个check方法接受不同类型的实体参数，实现类可能对不同类型有不同的处理逻辑
