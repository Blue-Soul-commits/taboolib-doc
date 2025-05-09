# ProxyCommandSender
## 基本信息 
- 类名和包路径: taboolib.common.platform.ProxyCommandSender
- 基本用途: 命令发送者的跨平台抽象接口，用于统一不同平台的命令发送者操作
- 类型: Kotlin 接口
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> origin: Any -> 获取原始平台的命令发送者对象
> name: String -> 命令发送者的名称
> isOp: Boolean -> 命令发送者是否拥有管理员权限，可读写属性

### 类方法
> isOnline(): Boolean -> 检查命令发送者是否在线
> sendMessage(message: String): Unit -> 向命令发送者发送消息
> performCommand(command: String): Boolean -> 让命令发送者执行指定命令
> hasPermission(permission: String): Boolean -> 检查命令发送者是否拥有指定权限
> cast<T>(): T -> 将原始对象转换为指定类型，如果类型不匹配则抛出异常
> castSafely<T>(): T? -> 安全地将原始对象转换为指定类型，如果类型不匹配则返回 null

## 实现细节
- 作为跨平台抽象接口，隐藏了不同平台（如 Bukkit、Bungee、Velocity 等）命令发送者的具体实现
- 提供了基本的命令发送者操作，如发送消息、执行命令、权限检查等
- 通过 origin 属性保存原始平台的命令发送者对象，可以通过 cast 方法转换回原始类型
- 实现类通常由 TabooLib 内部提供，针对不同平台有不同的实现

## 使用场景 
> 在跨平台插件中处理命令发送者，无需关心具体平台
> 在命令执行器中接收和操作命令发送者
> 向命令发送者发送消息或让其执行命令
> 检查命令发送者的权限或在线状态

## 注意事项 
> cast 方法在类型不匹配时会抛出 ClassCastException 异常，应谨慎使用
> 对于可能的类型转换错误，推荐使用 castSafely 方法进行安全转换
> 不同平台的原始对象类型不同，使用 origin 属性时需要注意平台兼容性
> isOp 属性在某些平台可能不完全支持修改操作
