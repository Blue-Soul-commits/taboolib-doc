# NbtHandler

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.handler.NbtHandler
- 基本用途: 物品NBT标签匹配处理器，检查物品的NBT数据是否符合指定条件
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
> check(item: ItemStack, value: String): Boolean -> 检查物品NBT标签是否符合给定条件字符串

## 实现细节
- 实现了ItemHandler接口，专门用于处理物品NBT数据的匹配逻辑
- 要求条件字符串必须以大括号"{}"包围，表示NBT格式
- 使用ParserUtils.parseNbt解析条件字符串，将其转换为键值对Map
- 使用TabooLib提供的getItemTag方法获取物品的NBT数据
- 对每个指定的NBT路径和值进行检查：
  - 使用getDeep方法根据路径获取NBT数据
  - 根据期望值的类型进行相应的类型转换和比较
  - 支持字符串、数字和布尔值类型的比较
- 要求所有指定的NBT条件都满足(all逻辑)，才返回true

## 使用场景
> 在物品匹配系统中验证物品的内部NBT数据
> 检查物品是否包含特定的自定义NBT标签
> 验证物品的高级属性，如耐久、附魔、特殊效果等
> 识别插件生成的特殊物品，这些物品通常包含额外的NBT数据
> 在插件开发中验证物品的内部状态

## 注意事项
> NBT条件必须使用特定格式：被大括号包围，如"{key1=value1&&key2=value2}"
> NBT路径支持深层次访问，使用点号分隔，如"display.Name"
> 只支持字符串、数字和布尔值类型的比较，其他类型会返回false
> 需要TabooLib提供的NMS支持，可能在不同的Minecraft版本上有不同的行为
> 在物品匹配系统中，通常需要注册此处理器到匹配器，以便通过名称调用
