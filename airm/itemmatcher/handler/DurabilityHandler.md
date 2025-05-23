# DurabilityHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.handler.DurabilityHandler
- 基本用途: 物品耐久度匹配处理器，检查物品的当前耐久度是否符合指定条件
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
> check(item: ItemStack, value: String): Boolean -> 检查物品耐久度是否符合给定条件字符串

## 实现细节
- 实现了ItemHandler接口，专门用于处理物品耐久度的匹配逻辑
- 首先检查物品类型是否具有耐久度（maxDurability > 0），若无则直接返回false
- 计算当前耐久度值为最大耐久度减去损耗值(maxDurability - item.durability)
- 使用ParserUtils.parseNumberCondition解析数值条件字符串
- 支持多种数值比较操作：
  - 大于等于(>=): 当前耐久度大于等于指定值
  - 小于等于(<=): 当前耐久度小于等于指定值
  - 大于(>): 当前耐久度大于指定值
  - 小于(<): 当前耐久度小于指定值
  - 等于(=或无操作符): 当前耐久度等于指定值

## 使用场景
> 在物品匹配系统中验证物品的当前耐久度
> 在物品交易或任务系统中检查工具/武器/装备的损耗程度
> 筛选出需要修复的物品
> 作为物品价值评估的一部分，与其他条件组合使用

## 注意事项
> 物品必须具有耐久度属性，否则匹配会直接返回false
> 计算的是当前剩余耐久度，而非损耗值
> 条件字符串需要遵循特定格式，如">50"、"<=100"或简单的数字"200"
> 使用ParserUtils解析条件，依赖于其解析逻辑和默认行为
> 在物品匹配系统中，通常需要注册此处理器到匹配器，以便通过名称调用
