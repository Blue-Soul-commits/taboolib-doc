# ExtraComponentLocation

## 基本信息
- 类名和包路径: taboolib.common.platform.command.ExtraComponentLocation
- 基本用途: 提供命令组件的位置相关扩展函数，用于简化命令树中坐标参数的处理
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> world(comment: String, suggest: List<String>, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层世界节点
> xyz(x: String, y: String, z: String, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层坐标 X,Y,Z 节点
> euler(yaw: String, pitch: String, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层坐标 YAW,PITCH 节点
> location(world: String, x: String, y: String, z: String, yaw: String, pitch: String, euler: Boolean, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层完整坐标节点
> locationWithoutWorld(x: String, y: String, z: String, yaw: String, pitch: String, euler: Boolean, optional: Boolean, permission: String, dynamic: CommandComponentDynamic.() -> Unit): CommandComponentDynamic -> 添加一层不含世界的坐标节点
> of(vararg elements: Any): List<String> -> 私有工具函数，将元素转换为字符串列表

### 类内可被访问字段
> 无类内可被访问字段（文件级扩展函数）

### 类方法
> 无类方法（文件级扩展函数）

## 实现细节
- 所有公开函数都是 CommandComponent 的扩展函数，返回 CommandComponentDynamic 类型
- world 函数创建世界参数节点，自动应用世界名称建议，默认包含 "~" 表示当前世界
- xyz 函数创建三个连续的数字参数节点，分别表示 X、Y、Z 坐标，支持相对坐标（~）
- euler 函数创建两个连续的数字参数节点，分别表示偏航角（yaw）和俯仰角（pitch），支持相对角度（~）
- location 函数组合了 world 和 xyz 函数，可选地包含 euler 函数，创建完整的位置参数
- locationWithoutWorld 函数组合了 xyz 函数，可选地包含 euler 函数，创建不含世界的位置参数
- 所有坐标相关函数都支持相对坐标，使用 "~" 表示相对于玩家当前位置
- of 函数是一个私有工具函数，用于将任意元素转换为字符串列表，主要用于建议列表生成

## 使用场景
> 构建需要位置参数的命令，如传送、放置方块等
> 支持绝对坐标和相对坐标（使用 ~ 符号）
> 提供完整的位置参数（世界、X、Y、Z、偏航角、俯仰角）或部分位置参数
> 简化游戏中常见的位置相关命令的构建

## 注意事项
> world 函数默认包含 "~" 建议，表示当前世界
> xyz 和 euler 函数使用 suggestionUncheck 允许输入不在建议列表中的值
> location 和 locationWithoutWorld 函数的 euler 参数控制是否包含偏航角和俯仰角
> 所有函数都支持 optional 参数，用于指定该参数是否可选
> 所有函数都支持 permission 参数，用于指定访问该参数需要的权限
> 使用这些函数时，通常需要配合 ExtraContextLocation 中的函数来解析参数值