# Conditions

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmatch.model.Conditions (包含MatchCondition, StringOperation, NumberOperator, CompoundType)
- 基本用途: 定义物品匹配系统的条件模型，用于表示和处理各种匹配条件
- 类型: 密封类(sealed class)和枚举(enum class)
- 所属模块: 物品匹配工具模块

## 类结构

### 公开静态字段
> 无显式定义的公开静态字段

### 公开静态方法
> 无显式定义的公开静态方法

### 类内可被访问字段
> MatchCondition:
> - modifiers: List<String> -> 条件的修饰符列表
>
> StringCondition:
> - operation: StringOperation -> 字符串操作类型
> - values: List<String> -> 字符串值列表
>
> NumberCondition:
> - operator: NumberOperator -> 数值操作符
> - value: Int -> 数值
> - tag: String -> 标签，默认为空字符串
>
> CompoundCondition:
> - type: CompoundType -> 复合条件类型
> - conditions: List<MatchCondition> -> 子条件列表

### 类方法
> 无额外的类方法

## 实现细节
- 使用Kotlin密封类(sealed class)定义条件层次结构，限制继承关系并支持详尽的when表达式
- 包含三种主要条件类型：
  1. StringCondition: 处理字符串比较，如精确匹配、包含、正则表达式等
  2. NumberCondition: 处理数值比较，如等于、大于、小于等
  3. CompoundCondition: 处理复合条件，可以组合多个条件进行AND、OR或NOT逻辑
- 使用枚举定义操作类型和运算符：
  - StringOperation: 定义字符串比较操作(EXACT, CONTAINS, REGEX, STARTS_WITH, ENDS_WITH)
  - NumberOperator: 定义数值比较操作(EQUAL, GREATER, LESS, GREATER_EQUAL, LESS_EQUAL)
  - CompoundType: 定义复合条件类型(ANY, ALL, NONE)，分别对应OR、AND和NOT逻辑
- 所有条件类型都支持修饰符(modifiers)，可能用于影响条件的处理方式
- NumberCondition额外包含tag字段，可用于标识数值的属性或来源

## 使用场景
> 构建物品匹配条件，用于判断物品是否符合特定要求
> 支持配置文件或命令输入中复杂条件的解析和表示
> 实现高度灵活的物品筛选系统，可组合多种条件类型
> 在物品匹配功能中作为核心数据模型，连接解析器和匹配器

## 注意事项
> 密封类的子类必须是MatchCondition的嵌套类或在同一文件中定义
> CompoundCondition可以无限嵌套，理论上可以构建任意复杂的条件树
> 使用时需要配合相应的解析器(Parser)将字符串条件转换为条件模型
> 当在when表达式中使用MatchCondition类型时，需处理所有子类型
> NumberCondition的tag字段初始默认为空字符串，使用前可能需要设置
