# LoreHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.handler.LoreHandler
- 基本用途: 物品Lore匹配处理器，检查物品的描述文本是否符合指定条件
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
> check(item: ItemStack, value: String): Boolean -> 检查物品Lore是否符合给定条件字符串
> private checkStringCondition(stringList: List<String>, condition: MatchCondition.StringCondition): Boolean -> 检查字符串条件
> private checkCompoundCondition(lore: List<String>, condition: MatchCondition.CompoundCondition): Boolean -> 检查复合条件

## 实现细节
- 实现了ItemHandler接口，专门用于处理物品Lore的匹配逻辑
- 使用ParserUtils.parseListCondition解析条件字符串，支持单个条件和复合条件
- 特殊处理：如果物品没有Lore且条件是"none"，则返回true
- 支持多种字符串操作类型：
  - EXACT: 完全匹配，Lore列表必须与条件值完全一致
  - CONTAINS: 包含匹配，Lore中任一行包含条件值中的任一项
  - REGEX: 正则表达式匹配，使用正则表达式检查Lore
  - STARTS_WITH: 开头匹配，Lore中任一行以条件值开头
  - ENDS_WITH: 结尾匹配，Lore中任一行以条件值结尾
- 支持条件修饰符：
  - uncolored/uc: 在匹配前移除颜色代码
  - lowercase/lc: 在匹配前转换为小写
- 支持复合条件：ANY(任一匹配)、ALL(全部匹配)、NONE(无一匹配)
- 字符串比较默认忽略大小写

## 使用场景
> 在物品匹配系统中验证物品的描述文本
> 检查物品是否包含特定的说明或属性描述
> 筛选具有特定文本特征的物品
> 在任务、成就或收藏系统中验证物品描述
> 识别特殊物品或稀有物品通过其描述文本

## 注意事项
> 物品必须有ItemMeta，否则匹配会直接返回false
> 如果物品没有Lore(lore为null或空列表)，只有条件为"none"时才会返回true
> 条件字符串支持多种格式和操作符，需要正确使用语法
> 支持多种条件组合，可以构建复杂的Lore匹配规则
> 正则表达式匹配可能会影响性能，尤其是对大量物品进行匹配时
> 在物品匹配系统中，通常需要注册此处理器到匹配器，以便通过名称调用
