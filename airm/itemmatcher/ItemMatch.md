# ItemMatch

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.ItemMatch
- 基本用途: 物品匹配系统的核心类，管理和执行物品匹配逻辑
- 类型: 具体类
- 所属模块: 物品匹配工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> handlers: ConcurrentHashMap<String, ItemHandler> -> 存储已注册的条件处理器

### 类方法
> registerHandler(name: String, handler: ItemHandler): Unit -> 注册一个条件处理器
> unregisterHandler(name: String): Unit -> 注销一个条件处理器
> match(itemStack: ItemStack, match: String): Boolean -> 检查物品是否匹配给定条件字符串
> matchTry(itemStack: ItemStack, match: String): Boolean -> 安全版本的match方法，捕获异常并返回false

## 实现细节
- 使用ConcurrentHashMap存储条件处理器，支持线程安全的并发访问
- 在初始化时自动注册所有预定义的处理器：
  - name: 物品名称匹配
  - lore: 物品描述匹配
  - nbt: 物品NBT数据匹配
  - enchant: 物品附魔匹配
  - flag: 物品标志匹配
  - material: 物品材质匹配
  - amount: 物品数量匹配
  - durability: 物品耐久度匹配
  - unbreakable: 物品不可破坏属性匹配
- 使用ParserUtils.splitConditions分割复合条件表达式
- 使用ParserUtils.parseKeyValue解析key:value格式的条件
- 支持将颜色代码应用到条件值(value.colored())
- 要求所有条件都匹配成功(all逻辑)才返回true
- 提供异常安全的matchTry方法，捕获匹配过程中可能出现的异常

## 使用场景
> 作为物品匹配系统的核心，统一管理多种条件处理器
> 检查物品是否符合由多个条件组成的复杂匹配规则
> 在配方系统、交易系统、任务系统中验证物品是否符合要求
> 支持插件开发者扩展自定义条件处理器
> 在物品过滤、分类和验证场景中使用

## 注意事项
> 条件字符串需要遵循特定格式：key:value形式，多个条件用分号(;)分隔
> 支持颜色代码在条件值中，使用&符号表示
> 处理器必须先注册，才能在条件中引用
> match方法可能会抛出异常，如果需要安全处理，应使用matchTry方法
> 由于使用ConcurrentHashMap，支持在多线程环境中安全使用
> 所有条件都必须满足才返回true，这是一个"与"(AND)的逻辑关系
