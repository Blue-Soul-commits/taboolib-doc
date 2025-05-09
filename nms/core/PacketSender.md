# PacketSender

## 基本信息
- 类名和包路径: taboolib.module.nms.PacketSender
- 基本用途: 提供向玩家发送 Minecraft 网络数据包的工具类
- 类型: 单例对象
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> useMinecraftMethod(): Unit -> 设置使用 Minecraft 方法发送数据包（已废弃）
> createBundlePacket(packets: List<Any>): Any? -> 创建数据包捆绑包（1.19.4+）
> sendPacket(player: Player, packet: Any): Unit -> 向指定玩家发送数据包
> getConnection(player: Player): Any -> 获取玩家的网络连接实例

### 类内可被访问字段
> playerConnectionMap: ConcurrentHashMap<String, Any> -> 缓存玩家名称到网络连接实例的映射
> sendPacketMethod: ClassMethod? -> 缓存发送数据包的反射方法
> newPacketBundlePacket: Constructor<*>? -> 缓存创建数据包捆绑包的构造函数
> useMinecraftMethod: Boolean -> 是否使用 Minecraft 方法发送数据包（已废弃）

### 类方法
> onJoin(e: PlayerJoinEvent): Unit -> 玩家加入时清除连接缓存
> onQuit(e: PlayerQuitEvent): Unit -> 玩家退出后延迟清除连接缓存

## 实现细节
- 使用 @Inject 和 @PlatformSide 注解标记为 Bukkit 平台的注入对象
- 通过反射获取和缓存玩家的网络连接实例
- 支持不同 Minecraft 版本的数据包发送方法（1.18+ 使用 "send"，早期版本使用 "sendPacket"）
- 支持创建数据包捆绑包（1.19.4+）
- 在玩家加入和退出时管理连接缓存
- 使用 ConcurrentHashMap 确保线程安全

## 使用场景
> 向玩家发送自定义数据包
> 实现不依赖于 Bukkit API 的高级功能
> 与 TabooLib 的数据包系统集成
> 支持数据包捆绑（1.19.4+），提高网络效率

## 注意事项
> 使用反射操作，可能因 Minecraft 版本更新而需要维护
> 缓存连接实例和方法以提高性能
> 在玩家退出时延迟清除缓存，避免潜在问题
> useMinecraftMethod 方法已被废弃（"没啥用了"）
