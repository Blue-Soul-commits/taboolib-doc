# LightInjectorImpl

## 基本信息
- 类名和包路径: taboolib.module.nms.LightInjectorImpl
- 基本用途: 实现 LightInjector 抽象类，提供数据包监听和处理功能，并集成 TabooLib 的事件系统
- 类型: 具体实现类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无额外可被访问字段（继承自 LightInjector 的字段）

### 类方法
> LightInjectorImpl(plugin: Plugin): void -> 初始化注入器并开始监听数据包
> onPacketReceiveAsync(sender: Player, channel: Channel, packet: Object): Object -> 当接收到数据包时异步调用，触发 PacketReceiveEvent 事件
> onPacketSendAsync(receiver: Player, channel: Channel, packet: Object): Object -> 当发送数据包时异步调用，触发 PacketSendEvent 事件

## 实现细节
- 继承自 LightInjector 抽象类，实现了数据包处理的核心方法
- 使用 TabooLib 的事件系统（PacketReceiveEvent 和 PacketSendEvent）处理数据包
- 支持处理有玩家和无玩家（握手阶段）的数据包
- 通过 ProtocolHandler 单例处理数据包的实际逻辑
- 当事件被取消时返回 null，导致数据包被丢弃

## 使用场景
> 监听和修改客户端与服务器之间的网络通信
> 实现基于事件的数据包处理系统
> 在不修改服务器核心代码的情况下实现高级网络功能
> 与 TabooLib 的事件系统集成，方便其他插件监听和处理数据包

## 注意事项
> 必须在主线程上构造 LightInjectorImpl 实例
> 每个插件只需要一个 LightInjectorImpl 实例即可
> 数据包处理在网络线程上异步进行，不要执行耗时操作
> 事件处理逻辑应该尽可能简单高效，避免影响服务器性能

