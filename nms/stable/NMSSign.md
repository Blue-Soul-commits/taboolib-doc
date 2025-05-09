# NMSSign

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSSign
- 基本用途: 提供跨版本的牌子编辑功能，允许捕获玩家对虚拟牌子的输入
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
> deserialize(component: Any): String -> 将聊天组件对象反序列化为字符串
> openSignEditor(player: Player, block: Block) -> 为玩家打开牌子编辑器

## 实现细节
- 使用 `nmsProxy<NMSSign>()` 创建代理实例，实际实现类为 `NMSSignImpl`
- 提供扩展函数 `Player.inputSign()` 简化使用
- 实现类 `NMSSignImpl` 根据不同的 Minecraft 版本使用不同的方法打开牌子编辑器
- 使用 `NMSSignListener` 监听玩家的牌子输入事件
- 支持从 1.8 到 1.21 版本的 Minecraft
- 在 1.20+ 版本中，使用带有 boolean 参数的构造函数创建 PacketPlayOutOpenSignEditor
- 在低版本中，使用不带 boolean 参数的构造函数
- 使用 `ConcurrentHashMap` 存储玩家名称与回调函数的映射
- 监听 `PlayerQuitEvent` 事件，在玩家退出时移除回调函数
- 监听 `PacketReceiveEvent` 事件，捕获玩家的牌子输入

## 使用场景
> 在需要获取玩家输入文本时使用，如创建命名牌、设置自定义名称等
> 在需要提供简单的文本输入界面时使用
> 在插件开发中需要跨版本兼容时使用

## 注意事项
> 不同版本的 Minecraft 对牌子编辑器的处理方式不同
> 在 1.20+ 版本中，PacketPlayOutOpenSignEditor 构造函数需要额外的 boolean 参数
> 在 1.20+ 版本中，虚拟牌子的 Y 坐标需要减去 2，而在低版本中需要设置为 0
> 在不同版本中，牌子的行数可能不同（3 行或 4 行）
> 使用 `sendBlockChange` 和 `sendSignChange` 方法创建虚拟牌子，不会影响实际的方块

