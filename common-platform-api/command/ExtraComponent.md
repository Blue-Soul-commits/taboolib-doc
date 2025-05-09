# ExtraComponent

## 基本信息
- 类名和包路径: taboolib.common.platform.command.ExtraComponent
- 基本用途: 提供命令组件的扩展函数，用于简化命令树构建过程中常见类型参数的处理
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> int(comment: String, suggest: List<String>, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层整型节点
> decimal(comment: String, suggest: List<String>, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层数字节点
> bool(comment: String, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层布尔值节点
> player(comment: String, suggest: List<String>, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层玩家节点

### 类内可被访问字段
> 无类内可被访问字段（文件级扩展函数）

### 类方法
> 无类方法（文件级扩展函数）

## 实现细节
- 所有函数都是 CommandComponent 的扩展函数，返回 CommandComponentDynamic 类型
- int 函数创建整型参数节点，如果没有提供建议列表则自动应用整型约束
- decimal 函数创建数字参数节点，如果没有提供建议列表则自动应用浮点数约束
- bool 函数创建布尔值参数节点，自动应用布尔值建议（true/false）
- player 函数创建玩家参数节点，自动应用在线玩家名称建议
- 所有函数都通过调用 dynamic 方法创建基础节点，然后应用特定的约束或建议
- 函数使用 also 块在创建节点后立即配置约束和建议

## 使用场景
> 构建需要特定类型参数的命令树
> 简化命令参数的类型约束和建议处理
> 提供类型安全的命令参数处理
> 快速构建具有常见参数类型（整数、小数、布尔值、玩家）的命令

## 注意事项
> 如果提供了 suggest 参数，则不会应用类型约束，而是使用提供的建议列表
> bool 函数不接受 suggest 参数，始终使用预定义的布尔值建议
> 所有函数都支持 optional 参数，用于指定该参数是否可选
> 所有函数都支持 permission 参数，用于指定访问该参数需要的权限
> 所有函数都支持 dynamic 参数，用于配置子节点或添加执行器
