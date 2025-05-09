# EntityMatch

## 基本信息
- 类名和包路径: top.maplex.arim.tools.entitymatch.EntityMatch
- 基本用途: 实体匹配系统的核心类，用于管理和执行各种实体匹配操作
- 类型: 具体类
- 所属模块: 实体匹配工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> handlers: ConcurrentHashMap<String, EntityHandler> -> 存储所有已注册的处理器

### 类方法
> registerHandler(name: String, handler: EntityHandler): Unit -> 注册一个实体匹配处理器
> unregisterHandler(name: String): Unit -> 注销一个实体匹配处理器
> match(entity: LivingEntity, match: String): Boolean -> 判断原版实体是否匹配给定条件
> matchTry(entity: LivingEntity, match: String): Boolean -> 安全版本的match方法，捕获异常并返回false
> match(entity: BaseEntityInstance, match: String): Boolean -> 判断自定义实体是否匹配给定条件
> matchTry(entity: BaseEntityInstance, match: String): Boolean -> 安全版本的自定义实体match方法，捕获异常并返回false

## 实现细节
- 使用线程安全的ConcurrentHashMap存储处理器，支持并发访问
- 在初始化时自动注册基础处理器，如名称、类型、元数据和生命值匹配
- 根据服务器已安装的插件自动注册额外处理器，例如Adyeshach和MythicMobs
- 匹配逻辑基于解析条件字符串，并要求所有条件都满足（逻辑与关系）
- 支持原版Bukkit实体和自定义实体两种匹配方法
- 提供了异常安全的匹配方法，避免匹配过程中的异常导致系统崩溃

## 使用场景
> 在需要根据复杂条件筛选实体时使用，例如任务系统、怪物掉落控制、技能触发条件等
> 作为实体相关插件的统一匹配接口，提供统一的条件语法和处理逻辑
> 支持多种实体系统，包括原版实体和自定义实体插件（如Adyeshach）

## 注意事项
> 条件字符串需要遵循特定格式：key:value形式，多个条件用空格分隔
> 匹配过程中可能抛出异常，建议使用matchTry方法进行安全匹配
> 支持彩色文本，条件值会通过colored()方法处理
> 可以通过注册自定义处理器来扩展匹配功能
