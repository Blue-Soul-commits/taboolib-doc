# GlowingBlockData

## 基本信息
- 类名和包路径: top.maplex.arim.tools.glow.internal.pojo.GlowingBlockData
- 基本用途: 存储方块发光效果的相关数据
- 类型: 数据类(class)
- 所属模块: 发光效果工具模块 - 内部数据结构

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> entityID: Int -> 用于发光效果的实体ID
> entityUUID: String -> 用于发光效果的实体UUID
> color: NamedTextColor -> 发光效果的颜色，可变属性
> mode: BlockGlowMode -> 方块发光的模式
> location: Location? -> 方块的位置，可空
> blockID: Int? -> 方块的ID，可空

### 类方法
> 无额外的类方法

## 实现细节
- 作为数据传输对象(DTO)，主要用于存储方块发光效果的相关数据
- 使用Adventure API的NamedTextColor表示发光颜色
- 字段color被声明为var，表示可以在创建对象后修改发光颜色
- 存储了生成发光效果所需的所有关键信息，包括实体ID、UUID、颜色、模式、位置和方块ID
- location和blockID字段为可空类型，表示在某些情况下这些信息可能不可用
- 不包含业务逻辑，纯粹作为数据载体使用

## 使用场景
> 在内部发光管理系统中跟踪和管理正在发光的方块
> 当需要修改已存在的方块发光效果时，存储必要的引用数据
> 在移除发光效果时，用于识别和定位需要清除的实体
> 在序列化/反序列化发光状态时使用，例如保存玩家可见的发光效果

## 注意事项
> 这是内部类(internal.pojo)，主要供发光系统内部使用
> entityID和entityUUID分别对应用于创建发光效果的实体的数字ID和字符串UUID
> 每个发光方块对应一个GlowingBlockData实例
> 修改color字段可以实时更新方块的发光颜色，而不需要重新创建发光效果
