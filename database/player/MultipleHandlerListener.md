# MultipleHandlerListener

## 基本信息
- 类名和包路径: taboolib.expansion.MultipleHandlerListener
- 基本用途: 监听玩家登录和退出事件，自动管理MultipleHandler的数据容器
- 类型: 单例对象(object)
- 所属模块: database-player

## 类结构

### 公开静态字段
> hooks: ArrayList<MultipleHandler> -> 存储所有注册的MultipleHandler实例

### 事件监听方法
> onPlayerJoin(event: PlayerJoinEvent): Unit -> 监听玩家登录事件
> onPlayerQuit(event: PlayerQuitEvent): Unit -> 监听玩家退出事件

## 实现细节
- 使用@Inject注解标记为TabooLib组件
- 使用@PlatformSide注解限制只在Bukkit平台生效
- 维护一个MultipleHandler列表，用于批量处理数据容器
- 当玩家登录时，为所有注册的MultipleHandler创建该玩家的数据容器
- 当玩家退出时，从所有注册的MultipleHandler中移除该玩家的数据容器
- 使用玩家的UUID字符串作为数据容器的标识符

## 使用场景
> 需要自动管理多个数据表的插件
> 需要在玩家登录和退出时自动处理数据容器的场景
> 作为MultipleHandler的事件监听组件

## 注意事项
> 只在Bukkit平台有效
> 需要将MultipleHandler实例添加到hooks列表中才能生效
> 使用玩家UUID作为数据容器的标识符，确保唯一性
> 这是一个自动化组件，通常不需要手动调用其方法
