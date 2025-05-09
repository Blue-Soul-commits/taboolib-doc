# NameHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.handler.NameHandler
- 基本用途: 物品名称匹配处理器，检查物品的显示名称是否符合指定条件
- 类型: 具体类(实现ItemHandler接口)
- 所属模块: 物品匹配工具模块 - 条件处理器

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> check(item: ItemStack, value: String): Boolean -> 检查物品名称是否符合给定条件字符串
> private checkStringCondition(string: String, condition: MatchCondition.StringCondition): Boolean -> 检查字符串条件

## 实现细节
- 实现了ItemHandler接口，专门用于处理物品名称的匹配逻辑
- 使用ParserUtils.parseListCondition解析条件字符串，支持单个条件和复合条件
- 检查物品是否有自定义显示名称(meta.hasDisplayName())，如果没有则直接返回false
- 支持多种字符串操作类型：
  - EXACT: 精确匹配，名称必须与条件值完全一致
  - CONTAINS: 包含匹配，名称包含条件值
  - REGEX: 正则表达式匹配，使用正则表达式检查名称
  - STARTS_WITH: 开头匹配，名称以条件值开头
  - ENDS_WITH: 结尾匹配，名称以条件值结尾
- 支持条件修饰符：
  - uncolored/uc: 在匹配前移除颜色代码
  - lowercase/lc: 在匹配前转换为小写
- 支持复合条件：ANY(任一匹配)、ALL(全部匹配)、NONE(无一匹配)
- 字符串比较默认忽略大小写

## 使用场景
> 在物品匹配系统中验证物品的自定义名称
> 筛选具有特定名称特征的物品
> 检查物品是否为特定的命名物品
> 在任务、收藏或成就系统中验证物品名称
> 识别特殊物品或稀有物品通过其命名

## 注意事项
> 物品必须有ItemMeta且有自定义显示名称，否则匹配会直接返回false
> 默认材质名称(未重命名的物品)不会被匹配，因为它们没有自定义显示名称
> 条件字符串支持多种格式和操作符，需要正确使用语法
> 支持多种条件组合，可以构建复杂的名称匹配规则
> 在使用正则表达式时需要注意性能影响
> 在物品匹配系统中，通常需要注册此处理器到匹配器，以便通过名称调用
