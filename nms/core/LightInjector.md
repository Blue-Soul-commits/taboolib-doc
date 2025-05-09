# LightInjector

## 基本信息
- 类名和包路径: taboolib.module.nms.LightInjector
- 基本用途: 一个轻量级但完整且快速的 Spigot 服务器数据包注入器，用于监听和处理网络数据包
- 类型: 抽象类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> plugin: Plugin -> 实例化此注入器的插件
> identifier: String -> 用于将 ChannelHandler 注册到通道管道中的标识符
> networkManagers: List<?> -> NetworkManager 的列表
> pendingNetworkManagers: Iterable<?> -> 在 Paper 服务器上，挂起的 NetworkManager 队列/列表
> listener: EventListener -> 事件监听器
> closed: AtomicBoolean -> 标记注入器是否已关闭
> playerCache: Map<UUID, Player> -> 用于允许 PacketHandlers 设置 player 字段的缓存
> injectedChannels: Set<Channel> -> 已注入通道的集合，用于加速通道注入

### 类方法
> LightInjector(plugin: Plugin): void -> 初始化注入器并开始监听数据包
> getIdentifier(): String -> 获取此注入器的唯一非空标识符
> onPacketReceiveAsync(sender: Player, channel: Channel, packet: Object): Object -> 当接收到数据包时异步调用
> onPacketSendAsync(receiver: Player, channel: Channel, packet: Object): Object -> 当发送数据包时异步调用
> sendPacket(receiver: Player, packet: Object): void -> 向玩家发送数据包
> sendPacket(channel: Channel, packet: Object): void -> 通过通道发送数据包
> receivePacket(sender: Player, packet: Object): void -> 模拟服务器从玩家接收到数据包
> receivePacket(channel: Channel, packet: Object): void -> 模拟服务器通过通道接收到数据包
> close(): void -> 关闭注入器并取消注入每个已注入的玩家
> isClosed(): boolean -> 返回此注入器是否已关闭
> getPlugin(): Plugin -> 返回实例化此注入器的插件

## 实现细节
- 使用 Netty 的 ChannelHandler 拦截和处理网络数据包
- 从 AsyncPlayerPreLoginEvent 事件开始监听数据包（大约从设置压缩数据包开始）
- 不监听状态 ping（即服务器列表 ping）期间交换的数据包
- 通过反射获取 Minecraft 服务器的网络管理器和通道
- 使用弱引用集合避免内存泄漏
- 支持 Paper 服务器上的挂起网络管理器队列/列表
- 在主线程上初始化，但数据包处理在网络线程上异步进行

## 使用场景
> 监听和修改客户端与服务器之间的网络通信
> 实现自定义网络协议或扩展现有协议
> 过滤或修改特定类型的数据包
> 在不修改服务器核心代码的情况下实现高级网络功能

## 注意事项
> 必须在主线程上构造 LightInjector 实例
> 每个插件只需要一个 LightInjector 实例即可
> 当插件禁用时，close() 方法会自动调用，但也可以手动调用
> 取消注入可能需要一些时间，因此在 close() 方法返回后，onPacketReceiveAsync 和 onPacketSendAsync 可能仍会被调用
> 不要在 onPacketReceiveAsync 和 onPacketSendAsync 方法中执行耗时操作，因为它们在网络线程上运行

