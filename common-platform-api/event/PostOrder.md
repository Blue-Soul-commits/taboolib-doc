# PostOrder
## 基本信息 
- 类名和包路径: taboolib.common.platform.event.PostOrder
- 基本用途: 定义 Velocity 平台事件监听器的执行顺序
- 类型: Kotlin 枚举类
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> FIRST -> 最先执行
> EARLY -> 较早执行
> NORMAL -> 正常执行顺序
> LATE -> 较晚执行
> LAST -> 最后执行

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> 无类内可被访问字段

### 类方法
> 无实例方法

## 实现细节
- 定义了五个标准的事件执行顺序，从先到后依次为：FIRST、EARLY、NORMAL、LATE、LAST
- 专为 Velocity 平台设计，对应 Velocity 事件系统中的 PostOrder 枚举
- 与 EventPriority 类似，但专用于 Velocity 平台的事件处理

## 使用场景 
> 在 Velocity 平台上注册事件监听器时指定执行顺序
> 控制 Velocity 代理服务器上多个插件之间事件处理的顺序
> 确保某些操作在其他插件之前或之后执行

## 注意事项 
> 仅适用于 Velocity 平台，其他平台（如 Bukkit、Bungee）应使用 EventPriority
> 执行顺序从先到后为：FIRST -> EARLY -> NORMAL -> LATE -> LAST
> 大多数情况下应使用 NORMAL 顺序，除非有特殊需求
> 在跨平台插件中，需要区分 Velocity 平台和其他平台的事件优先级处理