# PacketUtil

## 基本信息
- 类名和包路径: top.maplex.arim.tools.glow.internal.util.PacketUtil
- 基本用途: 提供发光效果所需的网络数据包工具方法
- 类型: 对象单例(object)，内部工具类
- 所属模块: 发光效果工具模块 - 内部工具

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法（扩展方法）
> Player.sendEntityMetadataPacket(entityID: Int, index: Int, type: EntityDataType<*>, dataItems: List<*>): Unit -> 发送实体元数据包
> Player.sendColorBasedTeamCreatePacket(color: NamedTextColor): Unit -> 发送创建基于颜色的团队数据包
> Player.sendColorBasedTeamDestroyPacket(color: NamedTextColor): Unit -> 发送销毁基于颜色的团队数据包
> Player.sendColorBasedTeamEntityAddPacket(teamID: String, color: NamedTextColor): Unit -> 发送添加实体到团队的数据包
> Player.sendColorBasedTeamEntityRemovePacket(teamID: String, color: NamedTextColor): Unit -> 发送从团队移除实体的数据包
> Player.sendCreateDummyFallingBlockOn(location: Location): Pair<Int, String>? -> 发送创建虚拟掉落方块的数据包
> Player.sendRemoveDummyFallingBlock(entityID: Int, blockLocation: Location, id: Int): Unit -> 发送移除虚拟掉落方块的数据包
> Player.sendCreateDummyEntityShulkerOn(location: Location): Pair<Int, String> -> 发送创建虚拟潜影贝的数据包
> Player.sendRemoveDummyEntityShulker(entityID: Int): Unit -> 发送移除虚拟潜影贝的数据包
> private NamedTextColor.toLowVersionChatColor(): ChatColor -> 将Adventure的颜色转换为低版本Bukkit的ChatColor

## 实现细节
- 使用PacketEvents库发送自定义数据包，避免直接使用NMS代码
- 采用Kotlin扩展函数设计，为Player类添加发送特定数据包的能力
- 实现了两种方块发光方式：掉落方块实体和潜影贝实体
- 利用团队系统(Scoreboard Teams)实现自定义颜色的发光效果
- 针对不同Minecraft版本提供不同的实现，确保跨版本兼容性
- 使用反射生成唯一的实体ID，避免与现有实体冲突
- 提供处理低版本(1.12.2)颜色显示问题的特殊方法

## 使用场景
> 在发光管理器中使用，实现实体和方块的发光效果
> 创建发光效果时，向客户端发送虚拟实体和团队操作数据包
> 修改发光颜色时，更新团队颜色或重新创建实体
> 移除发光效果时，清理虚拟实体和团队

## 注意事项
> 这是内部工具类(internal.util)，主要供发光系统内部使用
> 依赖PacketEvents库进行数据包操作，需确保正确配置依赖
> 掉落方块方式(STYLE模式)在1.18.2及更高版本不可用，因为这些版本限制了掉落方块的材质
> 针对低于1.19版本和1.19及以上版本，使用不同的实体生成数据包
> 大量使用注释说明版本兼容性问题和实现细节，包括对Mojang某些设计决策的吐槽
