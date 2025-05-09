# FlagHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.handler.FlagHandler
- 基本用途: 物品标志匹配处理器，检查物品是否具有指定的ItemFlag标志
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
> check(item: ItemStack, value: String): Boolean -> 检查物品是否具有指定的ItemFlag标志
> private checkCompoundCondition(meta: ItemMeta, condition: MatchCondition.CompoundCondition): Boolean -> 检查复合标志条件
> private checkSingleFlag(meta: ItemMeta, value: String): Boolean -> 检查单个标志条件

## 实现细节
- 实现了ItemHandler接口，专门用于处理物品ItemFlag标志的匹配逻辑
- 使用ParserUtils.parseListCondition解析条件字符串，支持单个标志和复合标志条件
- 支持两种主要条件类型：
  1. 单个字符串条件：检查物品是否具有特定的ItemFlag
  2. 复合条件：ANY(任一匹配)、ALL(全部匹配)、NONE(无一匹配)
- 在checkSingleFlag方法中，使用不区分大小写的匹配查找对应的ItemFlag
- 如果物品没有ItemMeta或找不到指定的ItemFlag，返回false
- 通过meta.hasItemFlag方法检查物品是否具有指定的标志

## 使用场景
> 在物品匹配系统中验证物品是否隐藏了特定属性或效果
> 检查物品是否配置了特定的显示设置，如隐藏附魔光芒
> 筛选具有特定UI表现的物品
> 检查物品是否符合特定的显示规范
> 在物品编辑或验证系统中使用

## 注意事项
> 标志名称必须与Bukkit的ItemFlag枚举值匹配，如HIDE_ENCHANTS、HIDE_ATTRIBUTES等
> 如果指定的标志名称不存在，条件匹配会返回false
> 物品必须有ItemMeta，否则匹配会直接返回false
> 条件字符串可以是简单的标志名称或复合条件，如"HIDE_ENCHANTS"或"any(HIDE_ENCHANTS,HIDE_ATTRIBUTES)"
> 标志名称匹配不区分大小写
> 在物品匹配系统中，通常需要注册此处理器到匹配器，以便通过名称调用
