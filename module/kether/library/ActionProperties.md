# ActionProperties

## 基本信息
- 类名和包路径: taboolib.library.kether.ActionProperties
- 基本用途: 提供预定义的脚本动作属性常量，用于在 Kether 脚本解析和执行过程中标记动作的特殊属性
- 类型: 工具类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> BLOCK: ParsedAction.ActionProperty<String> -> 用于指定动作所属的代码块名称
> ADDRESS: ParsedAction.ActionProperty<Integer> -> 用于标记动作在脚本中的地址或位置
> REQUIRE_FRAME: ParsedAction.ActionProperty<Boolean> -> 用于标记动作是否需要一个独立的执行帧

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段  

### 类方法
> 无类方法

## 实现细节
- 类中定义了三个静态常量，都是 ParsedAction.ActionProperty 类型的对象
- 使用 ParsedAction.ActionProperty.of() 工厂方法创建这些属性
- 这些属性用于在 ParsedAction 对象中存储和访问特定的元数据
- 属性值存储在 ParsedAction 的 properties 映射中，可通过 get/set 方法操作

## 使用场景
> 在 BlockReader 中标记代码块，当解析脚本时为动作设置其所属的代码块
> 在脚本执行引擎中标记动作的执行位置和特殊需求
> 在远程脚本执行时传递动作的属性信息

## 注意事项
> 这些属性通常不由用户直接操作，而是由脚本解析器和执行引擎内部使用
> 属性的值类型必须与声明的泛型类型匹配，否则可能导致类型转换异常
