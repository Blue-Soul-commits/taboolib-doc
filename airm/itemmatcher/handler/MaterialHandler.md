# MaterialHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.handler.MaterialHandler
- 基本用途: 物品材质匹配处理器，检查物品的材质类型是否符合指定条件
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
> check(item: ItemStack, value: String): Boolean -> 检查物品材质是否符合给定条件字符串

## 实现细节
- 实现了ItemHandler接口，专门用于处理物品材质的匹配逻辑
- 使用ParserUtils.parseStringCondition解析条件字符串，支持多种字符串操作
- 获取物品的材质名称(item.type.name)进行匹配
- 支持多种字符串操作类型：
  - EXACT: 精确匹配，材质名称必须与条件值完全一致
  - CONTAINS: 包含匹配，材质名称包含条件值
  - REGEX: 正则表达式匹配，使用正则表达式检查材质名称
  - STARTS_WITH: 开头匹配，材质名称以条件值开头
  - ENDS_WITH: 结尾匹配，材质名称以条件值结尾
- 所有比较都忽略大小写
- 对于多个条件值(values列表)，使用any逻辑，只要匹配任一个值即返回true

## 使用场景
> 在物品匹配系统中验证物品的基本材质类型
> 筛选特定类别的物品，如所有剑类或所有木质物品
> 检查物品是否属于某个特定材质组
> 在配方系统、交易系统或任务系统中验证物品类型
> 与其他条件组合使用，构建复杂的物品匹配规则

## 注意事项
> 材质名称使用Bukkit的Material.name，为大写带下划线的格式，如"DIAMOND_SWORD"
> 所有匹配操作都忽略大小写，所以"diamond_sword"和"DIAMOND_SWORD"视为相同
> 使用CONTAINS操作时要注意可能会产生意外匹配，例如"WOOD"会匹配到"WOODEN_SWORD"
> 正则表达式匹配可能会影响性能，尤其是对大量物品进行匹配时
> 在物品匹配系统中，通常需要注册此处理器到匹配器，以便通过名称调用
