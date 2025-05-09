# SubscribeEvent
## 基本信息 
- 类名和包路径: taboolib.common.platform.event.SubscribeEvent
- 基本用途: 标记方法为事件监听器，用于注册跨平台的事件处理函数
- 类型: Kotlin 注解类
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> priority: EventPriority -> 事件处理的优先级，默认为 EventPriority.NORMAL
> ignoreCancelled: Boolean -> 是否忽略已取消的事件，默认为 false
> level: Int -> BungeeCord 平台特有的事件级别，默认为 -1
> postOrder: PostOrder -> Velocity 平台特有的事件处理顺序，默认为 PostOrder.NORMAL
> bind: String -> 用于 OptionalEvent 的绑定标识符，默认为空字符串

### 类方法
> 无实例方法（注解类）

## 实现细节
- 使用 @Target(AnnotationTarget.FUNCTION) 标记，表示该注解只能应用于方法
- 使用 @Retention(AnnotationRetention.RUNTIME) 标记，表示该注解在运行时可通过反射获取
- 提供了多个参数用于配置事件监听器的行为：
  - priority: 控制在 Bukkit 等平台上的事件处理优先级
  - ignoreCancelled: 控制是否处理已被其他插件取消的事件
  - level: 专用于 BungeeCord 平台的事件级别设置
  - postOrder: 专用于 Velocity 平台的事件处理顺序
  - bind: 用于绑定 OptionalEvent（可选事件）的标识符
- 由 TabooLib 内部的事件处理系统识别和管理，自动注册到相应平台

## 使用场景 
> 注册跨平台的事件监听方法
> 控制事件处理的优先级和行为
> 在不同平台上统一事件处理机制
> 处理可选事件（OptionalEvent）

## 注意事项 
> 被注解的方法应该有且仅有一个参数，类型为要监听的事件类
> priority 和 ignoreCancelled 主要用于 Bukkit 平台
> level 参数仅在 BungeeCord 平台有效
> postOrder 参数仅在 Velocity 平台有效
> bind 参数用于处理可能不存在的事件类（OptionalEvent）