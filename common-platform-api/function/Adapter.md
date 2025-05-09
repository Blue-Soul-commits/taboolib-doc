# Adapter
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.Adapter
- 基本用途: 提供跨平台适配功能的顶层函数集合，简化对 PlatformAdapter 服务的访问
- 类型: Kotlin 文件，包含顶层函数
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段（文件级别）

### 公开静态方法 
> console(): ProxyCommandSender -> 获取控制台命令发送者
> adaptCommandSender(any: Any): ProxyCommandSender -> 将平台特定的命令发送者转换为跨平台命令发送者
> onlinePlayers(): List<ProxyPlayer> -> 获取所有在线玩家
> adaptPlayer(any: Any): ProxyPlayer -> 将平台特定的玩家对象转换为跨平台玩家对象
> getProxyPlayer(name: String): ProxyPlayer? -> 通过名称获取玩家，不区分大小写
> getProxyPlayer(uuid: UUID): ProxyPlayer? -> 通过 UUID 获取玩家
> adaptLocation(any: Any): Location -> 将平台特定的位置对象转换为跨平台位置对象
> platformLocation<T>(location: Location): T -> 将跨平台位置对象转换为平台特定的位置对象
> allWorlds(): List<String> -> 获取所有世界的名称列表

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有函数都是顶层函数，可以直接导入使用，无需通过类实例调用
- 内部通过 PlatformFactory.getService<PlatformAdapter>() 获取平台适配器服务实例
- 提供了对 PlatformAdapter 接口方法的简便访问，减少重复代码
- 增加了两个额外的实用函数 getProxyPlayer，用于通过名称或 UUID 查找玩家
- platformLocation 函数使用泛型和类型转换，简化了跨平台位置对象到平台特定位置对象的转换

## 使用场景 
> 获取控制台对象和在线玩家列表
> 在跨平台代码中查找和操作玩家
> 转换平台特定对象和跨平台对象
> 处理位置信息和世界数据

## 注意事项 
> 这些函数依赖于 PlatformAdapter 服务，确保在适当的生命周期阶段调用
> adaptPlayer 和 adaptCommandSender 函数在传入类型不匹配时可能抛出异常
> getProxyPlayer 函数返回可空类型，调用时需要处理 null 情况
> platformLocation 函数使用了不安全的类型转换，使用时需确保类型正确
