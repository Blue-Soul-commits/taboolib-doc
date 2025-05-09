# KetherScriptLoader

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherScriptLoader
- 基本用途: Kether脚本的自定义加载器，扩展SimpleQuestLoader，实现特有的语法解析和容错功能
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> newBlockReader(content: CharArray, service: QuestService<*>, namespace: MutableList<String>): BlockReader -> 创建自定义的代码块读取器

## 实现细节
- KetherScriptLoader继承自SimpleQuestLoader，重写了newBlockReader方法
- 提供了自定义的BlockReader匿名内部类实现，重写newActionReader方法
- 内部类Reader继承自SimpleReader，专门处理Kether特有的语法规则
- Reader重写了nextToken和nextTokenBlock方法，用于处理转义空格(\\s)
- Reader重写了nextAction方法，实现了Kether特有的语法解析逻辑：
  - 以'{'开头的内容解析为匿名动作块
  - 以'&'开头的内容解析为变量获取(ActionGet)，支持属性访问语法(变量[属性])
  - 以'*'开头的内容解析为字面量(ActionLiteral)
  - 其他情况尝试作为动作名称解析，支持属性访问语法(对象[属性])
- 实现了宽容解析模式，当Kether.isAllowToleranceParser为true时，未知的动作会被解析为字面量，而不是抛出异常

## 使用场景
> 作为Kether脚本的核心解析器，处理脚本文本到动作对象的转换
> 支持扩展的Kether语法，如变量访问(&variable)和属性访问(object[property])
> 实现容错解析，提高脚本编写的灵活性
> 通过自定义Reader处理特殊的语法规则和转义字符

## 注意事项
> 宽容解析模式(Kether.isAllowToleranceParser)默认开启，可以简化脚本语法
> 在宽容模式下，未知的动作名称会被解析为字面量，可能导致意外行为
> 属性访问语法(object[property])依赖ActionProperty实现，支持动态属性获取
> 使用反射(setProperty)临时修改blockParser的index，可能导致兼容性问题