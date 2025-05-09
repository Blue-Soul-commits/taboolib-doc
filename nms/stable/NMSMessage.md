# NMSMessage

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSMessage
- 基本用途: 提供跨版本的 JSON 格式消息处理功能
- 类型: 抽象类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> instance: NMSMessage -> 通过 nmsProxy 懒加载的单例实例

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> fromJson(json: String): Any -> 将 JSON 格式的消息转换为 NMS 对象
> setRawTitle(bossBar: BossBar, title: String) -> 将 JSON 格式的消息设置为 BossBar 的标题
> sendRawTitle(player: Player, title: String?, subtitle: String?, fadein: Int, stay: Int, fadeout: Int) -> 发送 JSON 格式的标题和副标题到玩家
> sendRawActionBar(player: Player, action: String) -> 发送 JSON 格式的动作栏消息到玩家

## 实现细节
- 使用 `nmsProxy<NMSMessage>()` 创建代理实例，实际实现类为 `NMSMessageImpl`
- 通过 `unsafeLazy` 延迟初始化单例实例
- 提供三个扩展函数简化使用：`BossBar.setRawTitle()`、`Player.sendRawTitle()` 和 `Player.sendRawActionBar()`
- 实现类 `NMSMessageImpl` 根据不同的 Minecraft 版本使用不同的方法处理 JSON 格式的消息
- 使用 `typealias` 简化不同版本 NMS 类的引用
- 支持从 1.8 到 1.21 版本的 Minecraft，对于低于 1.9 的版本，标题功能会抛出 `UnsupportedVersionException`

## 使用场景
> 在需要发送富文本消息到玩家的标题栏、副标题栏或动作栏时使用
> 在需要设置 BossBar 的富文本标题时使用
> 在插件开发中需要跨版本兼容时使用

## 注意事项
> 不同版本的 Minecraft 对消息的处理方式不同，特别是 1.16+ 版本中 ChatSerializer.a 的返回值变化
> 在 1.20.5+ 版本中，BossBar 的处理方式有所不同
> 标题功能仅支持 1.9+ 版本的 Minecraft
> 动作栏消息优先使用 Spigot API，如果失败则回退到发送数据包的方式

