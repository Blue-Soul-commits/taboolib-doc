# DataSerializerFactoryLegacy

## 基本信息
- 类名和包路径: taboolib.module.nms.DataSerializerFactoryLegacy
- 基本用途: 为 Minecraft 1.20.4 及以下版本提供数据序列化功能
- 类型: 实现类
- 所属模块: bukkit-nms-data-serializer

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> buf: ByteBuf -> 用于数据序列化的缓冲区

### 类方法
> writeByte(byte: Byte): DataSerializer -> 写入一个字节
> writeBytes(bytes: ByteArray): DataSerializer -> 写入字节数组
> writeShort(short: Short): DataSerializer -> 写入短整型
> writeInt(int: Int): DataSerializer -> 写入整型
> writeLong(long: Long): DataSerializer -> 写入长整型
> writeFloat(float: Float): DataSerializer -> 写入浮点型
> writeDouble(double: Double): DataSerializer -> 写入双精度浮点型
> writeBoolean(boolean: Boolean): DataSerializer -> 写入布尔值
> writeMetadataLegacy(meta: List<Any>): DataSerializer -> 写入旧版元数据
> writeComponent(json: String): DataSerializer -> 写入聊天组件
> build(): Any -> 构建并返回底层缓冲区
> dataOutput(): DataOutput -> 获取数据输出流
> newSerializer(): DataSerializer -> 创建新的序列化器实例

## 实现细节
- 实现了 DataSerializerFactory 和 DataSerializer 接口
- 使用 PacketDataSerializer 作为底层缓冲区
- 所有写入方法都返回 this，支持链式调用
- writeMetadataLegacy 方法使用 DataWatcher.a 方法处理旧版元数据
- writeComponent 方法根据 Minecraft 版本使用不同的序列化方式：
  - 1.20.3+ 版本使用 ComponentSerialization.CODEC 编码聊天组件
  - 1.20.2 及以下版本直接使用 writeUtf 方法

## 使用场景
> 序列化数据以便在网络上传输
> 创建自定义数据包
> 处理实体元数据
> 支持旧版本 Minecraft 的数据序列化

## 注意事项
> 此实现专为 Minecraft 1.20.4 及以下版本设计
> writeComponent 方法根据 Minecraft 版本使用不同的实现
> writeMetadataLegacy 方法需要传入 DataWatcher.Item 类型的列表

