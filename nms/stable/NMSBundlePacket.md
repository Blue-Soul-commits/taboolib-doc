# NMSBundlePacket

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSBundlePacket
- 基本用途: 处理 Minecraft 1.19.4+ 版本中的 BundlePacket 数据包
- 类型: 抽象类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> readPackets(packet: Any): MutableIterable<Any> -> 读取 BundlePacket 中的子数据包

## 实现细节
- 通过 `nmsProxy<NMSBundlePacket>()` 获取实现类的实例
- 实现类 `NMSBundlePacketImpl` 使用 `ClientboundBundlePacket.subPackets()` 方法获取子数据包
- 提供了三个扩展函数来简化 BundlePacket 的操作:
  - `Packet.isBundlePacket()`: 判断数据包是否为 BundlePacket
  - `Packet.subPackets()`: 获取 BundlePacket 中的子数据包
  - `List<Packet>.createBundlePacket()`: 将多个数据包打包成一个 BundlePacket

## 使用场景
> 在需要处理 Minecraft 1.19.4+ 版本中的 BundlePacket 数据包时使用
> 在数据包监听器中解析接收到的 BundlePacket
> 在发送多个数据包时，将它们打包成一个 BundlePacket 以提高效率

## 注意事项
> 仅适用于 Minecraft 1.19.4 及以上版本，因为 BundlePacket 是在这个版本引入的
> 在低版本中使用会导致 `ClassNotFoundException`
> 使用 `createBundlePacket()` 时，如果无法创建 BundlePacket，会抛出异常
