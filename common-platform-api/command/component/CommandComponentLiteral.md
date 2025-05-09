# CommandComponentLiteral

## 基本信息
- 类名和包路径: taboolib.common.platform.command.component.CommandComponentLiteral
- 基本用途: 明文命令组件，用于表示固定的命令参数或子命令
- 类型: 类（继承自 CommandComponent）
- 所属模块: TabooLib 平台命令组件模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> aliases: Array<String> -> 命令别名数组
> hidden: Boolean -> 是否在命令补全中隐藏该命令

### 类方法
> toString(): String -> 返回组件的字符串表示

## 实现细节
- 继承自 CommandComponent，专门用于处理固定文本参数
- 支持多个别名，允许用户使用任意一个别名触发该命令
- 可以设置为隐藏，在命令补全中不会显示
- 通过 index、optional 和 permission 参数继承自父类的功能

## 使用场景
> 定义子命令，如 "help"、"reload" 等
> 创建具有多个别名的命令，提高用户体验
> 创建隐藏命令，用于管理或调试功能

## 注意事项
> aliases 数组包含所有可用的命令别名，区分大小写
> hidden 为 true 时，该命令在补全列表中不会显示，但仍然可以使用
> 作为 CommandComponent 的子类，可以拥有自己的子组件和执行器