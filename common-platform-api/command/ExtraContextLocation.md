# ExtraContextLocation

## 基本信息
- 类名和包路径: taboolib.common.platform.command.ExtraContextLocation
- 基本用途: 提供命令上下文的位置相关扩展函数，用于从命令参数中获取并转换位置信息
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> world(id: String, origin: Location?): String -> 获取世界参数
> worldOrNull(id: String, origin: Location?): String? -> 获取世界参数，可能返回 null
> x(id: String, origin: Location?): Double -> 获取 X 坐标参数
> y(id: String, origin: Location?): Double -> 获取 Y 坐标参数
> z(id: String, origin: Location?): Double -> 获取 Z 坐标参数
> yaw(id: String, origin: Location?): Float -> 获取偏航角参数
> yawOrNull(id: String, origin: Location?): Float? -> 获取偏航角参数，可能返回 null
> pitch(id: String, origin: Location?): Float -> 获取俯仰角参数
> pitchOrNull(id: String, origin: Location?): Float? -> 获取俯仰角参数，可能返回 null
> location(world: String, x: String, y: String, z: String, yaw: String, pitch: String, origin: Location?): Location -> 获取完整位置参数
> locationWithoutWorld(x: String, y: String, z: String, yaw: String, pitch: String, origin: Location?): Location -> 获取不带世界的位置参数

### 类内可被访问字段
> 无类内可被访问字段（文件级扩展函数）

### 类方法
> 无类方法（文件级扩展函数）

## 实现细节
- 所有函数都是 CommandContext<T> 的泛型扩展函数，适用于任何类型的命令上下文
- 支持相对坐标表示法，使用 "~" 表示相对于原点（通常是玩家位置）的坐标
- world 和 worldOrNull 函数处理世界参数，支持 "~" 表示当前世界
- x、y、z 函数处理坐标参数，支持 "~" 表示相对坐标
- yaw、yawOrNull、pitch、pitchOrNull 函数处理角度参数，支持 "~" 表示相对角度
- location 函数组合所有参数创建完整的位置对象
- locationWithoutWorld 函数使用玩家当前世界创建位置对象
- 所有函数都支持自定义原点参数，默认使用玩家位置作为原点
- 私有扩展函数 double() 和 float() 用于安全转换字符串，转换失败时返回默认值

## 使用场景
> 在命令执行器中获取并转换位置相关参数
> 支持相对坐标系统，类似 Minecraft 原生命令
> 处理传送、方块放置等需要位置信息的命令
> 与 ExtraComponentLocation 中的函数配合使用，实现完整的位置参数处理
> 在复杂命令中获取多个不同部分的位置信息

## 注意事项
> 非 Null 版本的函数在参数不存在或转换失败时可能抛出异常
> Null 版本的函数在参数不存在时返回 null
> 相对坐标使用 "~" 前缀，如 "~", "~10", "~-5"
> 空的相对坐标 "~" 表示不偏移，即原点的对应坐标
> 使用 origin 参数可以指定自定义原点，默认使用玩家位置
> 参数名称应该与命令定义时使用的参数名称一致
> 这些函数通常与 ExtraComponentLocation 中的位置节点函数配合使用
