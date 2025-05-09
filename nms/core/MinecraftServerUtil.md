# MinecraftServerUtil

## 基本信息
- 文件路径: module/bukkit-nms/src/main/kotlin/taboolib/module/nms/MinecraftServerUtil.kt
- 基本用途: 提供 Minecraft 服务器相关工具函数和 NMS 代理功能
- 类型: 工具函数集合
- 所属模块: bukkit-nms

## 文件结构

### 私有字段
> nmsProxyClassMap: ConcurrentHashMap<String, Class<?>> -> 缓存 NMS 代理类
> nmsProxyInstanceMap: ConcurrentHashMap<String, Any> -> 缓存 NMS 代理实例
> packetPool: ConcurrentHashMap<String, ExecutorService> -> 玩家数据包发送线程池

### 公开属性
> isBukkitServerRunning: Boolean -> 检查 Bukkit 服务器是否在运行
> minecraftServerObject: Any -> 获取 MinecraftServer 实例

### 公开函数
> obcClass(name: String): Class<?> -> 获取 OBC 类
> nmsClass(name: String): Class<?> -> 获取 NMS 类
> nmsProxy<T>(clazz: Class<T>, bind: String, vararg parameter: Any): T -> 创建 NMS 代理实例
> nmsProxy<T>(clazz: Class<T>, bind: String, parent: List<String>, vararg parameter: Any): T -> 创建 NMS 代理实例（带父类）
> nmsProxy<T>(bind: String, vararg parameter: Any): T -> 创建 NMS 代理实例（内联版本）
> nmsProxy<T>(bind: String, parent: List<String>, vararg parameter: Any): T -> 创建 NMS 代理实例（内联版本，带父类）
> nmsProxyClass<T>(clazz: Class<T>, bind: String, parent: List<String>): Class<T> -> 获取 NMS 代理类
> nmsProxyClass<T>(clazz: Class<T>, bind: String): Class<T> -> 获取 NMS 代理类
> nmsProxyClass<T>(bind: String, parent: List<String>): Class<T> -> 获取 NMS 代理类（内联版本）

### 扩展函数
> Player.sendBundlePacket(vararg packet: Any): CompletableFuture<Void> -> 向玩家异步发送打包数据包
> Player.sendBundlePacket(packet: List<Any>): CompletableFuture<Void> -> 向玩家异步发送打包数据包
> Player.sendPacket(packet: Any): CompletableFuture<Void> -> 向玩家异步发送数据包
> Player.sendBundlePacketBlocking(vararg packet: Any): Unit -> 向玩家同步发送打包数据包
> Player.sendBundlePacketBlocking(packet: List<Any>): Unit -> 向玩家同步发送打包数据包
> Player.sendPacketBlocking(packet: Any): Unit -> 向玩家同步发送数据包

### 内部类
> PoolListener -> 管理玩家数据包线程池的事件监听器

## 实现细节
- 使用 ConcurrentHashMap 缓存 NMS 代理类和实例，提高性能
- 通过 AsmClassTranslation 动态生成代理类，处理不同 Minecraft 版本的兼容性
- 为每个玩家创建独立的线程池，用于异步发送数据包
- 支持 1.19.4+ 的数据包捆绑功能
- 在玩家加入和退出时管理线程池资源

## 使用场景
> 获取 Minecraft 服务器相关类和实例
> 创建跨版本兼容的 NMS 代理对象
> 向玩家发送自定义数据包
> 实现高级功能，如自定义物品、实体、GUI 等

## 注意事项
> nmsProxy 函数会缓存创建的实例，相同参数的多次调用会返回同一个实例
> 异步发送数据包时使用独立线程池，避免阻塞主线程
> 在玩家退出时会关闭对应的线程池，释放资源
> 代理类生成依赖于 AsmClassTranslation，需要相应的实现类存在

