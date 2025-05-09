# PacketSendEvent

## 基本信息
- 类名和包路径: taboolib.module.nms.PacketSendEvent
- 基本用途: 表示服务器向客户端发送数据包的事件，可用于监听和拦截数据包
- 类型: 事件类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> player: Player -> 接收数据包的玩家
> packet: Packet -> 要发送的数据包对象

### 内部类
> Handshake -> 用于早期登录/状态数据包的特殊事件类型
  - channel: Channel -> 网络通道
  - packet: Packet -> 要发送的数据包对象

## 实现细节
- 继承自 CancelableInternalEvent，支持取消事件（拦截数据包）
- 提供对发送的数据包和接收者的访问
- 包含 Handshake 内部类，用于处理早期登录阶段的数据包（此时玩家对象尚未创建）
- 由 LightInjectorImpl 在发送数据包时触发

## 使用场景
> 监听服务器发送到客户端的数据包
> 拦截和修改服务器发送的数据包
> 实现自定义网络功能，如数据包过滤、内容修改等
> 处理早期登录阶段的数据包（通过 Handshake 内部类）

## 注意事项
> 自 TabooLib 6.2 版本起，不能放行已被拦截的数据包（即使用 isCancelled = false）
> 事件处理应尽量高效，避免影响网络性能
> 修改或拦截关键数据包可能会导致客户端异常
> 对于早期登录阶段的数据包，应使用 Handshake 内部类
