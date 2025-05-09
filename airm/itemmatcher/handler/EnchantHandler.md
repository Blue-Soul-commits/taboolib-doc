# EnchantHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.handler.EnchantHandler
- 基本用途: 物品附魔匹配处理器，检查物品的附魔是否符合指定条件
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
> check(item: ItemStack, value: String): Boolean -> 检查物品附魔是否符合给定条件字符串
> private checkCompoundCondition(item: ItemStack, condition: MatchCondition.CompoundCondition): Boolean -> 检查复合附魔条件
> private checkCondition(item: ItemStack, condition: MatchCondition): Boolean -> 检查单个附魔条件

## 实现细节
- 实现了ItemHandler接口，专门用于处理物品附魔的匹配逻辑
- 使用ParserUtils.parseNumberListCondition解析条件字符串，支持复杂的条件组合
- 支持两种主要条件类型：
  1. 简单数值条件：指定附魔类型和等级要求
  2. 复合条件：ANY(任一匹配)、ALL(全部匹配)、NONE(无一匹配)
- 对于数值条件，使用tag字段存储附魔类型名称，通过Enchantment.getByName获取对应附魔
- 支持多种数值比较操作：
  - 大于等于(>=): 附魔等级大于等于指定值
  - 小于等于(<=): 附魔等级小于等于指定值
  - 大于(>): 附魔等级大于指定值
  - 小于(<): 附魔等级小于指定值
  - 等于(=或无操作符): 附魔等级等于指定值
- 通过递归处理复合条件，实现灵活的条件组合

## 使用场景
> 在物品匹配系统中验证物品的附魔属性
> 检查物品是否具有特定类型和等级的附魔
> 筛选具有特定附魔组合的物品
> 判断武器或装备是否满足特定附魔要求
> 在交易、任务或奖励系统中验证物品附魔

## 注意事项
> 附魔名称必须使用Minecraft的内部名称，如SHARPNESS、EFFICIENCY
> 如果指定的附魔类型不存在，条件匹配会返回false
> 条件字符串需要遵循特定格式，如"SHARPNESS>=3"、"PROTECTION=4"
> 对于复合条件，格式为"any(SHARPNESS>3,LOOTING>2)"等
> 使用ParserUtils解析条件，依赖于其解析逻辑和默认行为
> 在物品匹配系统中，通常需要注册此处理器到匹配器，以便通过名称调用
