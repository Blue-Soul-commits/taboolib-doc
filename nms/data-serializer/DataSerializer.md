# DataSerializer

## 基本信息
- 类名和包路径: taboolib.module.nms.DataSerializer
- 基本用途: 提供 Minecraft 数据序列化的通用接口
- 类型: 接口
- 所属模块: bukkit-nms-data-serializer

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 抽象方法
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
> build(): Any -> 构建并返回底层数据结构
> dataOutput(): DataOutput -> 获取数据输出流

### 默认实现方法
> writeUUID(uuid: UUID): DataSerializer -> 写入 UUID
> writeBlockPosition(x: Int, y: Int, z: Int): DataSerializer -> 写入方块位置
> writeVarIntArray(intArray: IntArray): DataSerializer -> 写入变长整型数组
> writeVarInt(int: Int): DataSerializer -> 写入变长整型
> writeNullable(value: T?, writer: (T) -> Unit): DataSerializer -> 写入可空值
> writeEnumSet(enumSet: EnumSet<E>, enumClass: Class<E>): DataSerializer -> 写入枚举集合
> writeFixedBitSet(bitSet: BitSet, size: Int): DataSerializer -> 写入固定大小的位集合
> writeString(string: String): DataSerializer -> 写入字符串
> writeUtf(string: String, length: Int = 32767): DataSerializer -> 写入 UTF 字符串
> writeGameProfileProperties(map: ForwardingMultimap<*, *>): DataSerializer -> 写入游戏配置文件属性

## 实现细节
- 所有方法都返回 this，支持链式调用
- writeUUID 方法将 UUID 拆分为最高有效位和最低有效位写入
- writeBlockPosition 方法使用位运算将三个坐标压缩到一个长整型中
- writeVarInt 方法实现了变长整型编码
- writeFixedBitSet 方法确保位集合不超过指定大小
- writeString 和 writeUtf 方法都会检查字符串长度，防止超出限制
- writeGameProfileProperties 方法用于序列化游戏配置文件的属性

## 使用场景
> 序列化数据以便在网络上传输
> 创建自定义数据包
> 处理实体元数据
> 提供跨 Minecraft 版本的数据序列化接口

## 注意事项
> writeMetadataLegacy 方法仅适用于 1.19.3 之前的版本
> 字符串长度有限制，超出会抛出 EncoderException
> 实现类需要提供所有抽象方法的实现

