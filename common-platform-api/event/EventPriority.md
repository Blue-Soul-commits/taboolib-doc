# EventPriority
## 基本信息 
- 类名和包路径: taboolib.common.platform.event.EventPriority
- 基本用途: 定义事件监听器的优先级，用于控制事件处理的顺序
- 类型: Kotlin 枚举类
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> LOWEST(level: -64) -> 最低优先级
> LOW(level: -32) -> 低优先级
> NORMAL(level: 0) -> 正常优先级
> HIGH(level: 32) -> 高优先级
> HIGHEST(level: 64) -> 最高优先级
> MONITOR(level: 128) -> 监控优先级

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> level: Int -> 优先级的数值表示，用于比较优先级的高低

### 类方法
> 无实例方法

## 实现细节
- 定义了六个标准的事件优先级，从低到高依次为：LOWEST、LOW、NORMAL、HIGH、HIGHEST、MONITOR
- 每个优先级都有一个对应的整数值（level），用于在内部比较优先级的高低
- 优先级数值间隔为 32，便于在必要时插入自定义优先级
- NORMAL 优先级的数值为 0，作为标准参考点
- MONITOR 优先级特别高，通常用于监控事件而不修改事件

## 使用场景 
> 在注册事件监听器时指定处理优先级
> 控制多个插件之间事件处理的顺序
> 确保某些关键操作在其他插件之前或之后执行
> 使用 MONITOR 优先级监控事件的最终状态

## 注意事项 
> 优先级从低到高的执行顺序为：LOWEST -> LOW -> NORMAL -> HIGH -> HIGHEST -> MONITOR
> MONITOR 优先级应仅用于监控事件，不应修改事件状态或取消事件
> 大多数情况下应使用 NORMAL 优先级，除非有特殊需求
> 过度依赖优先级可能导致插件间的兼容性问题
