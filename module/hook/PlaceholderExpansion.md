# PlaceholderExpansion
## 基本信息
- 类名和包路径: taboolib.platform.compat.PlaceholderExpansion
- 基本用途: 提供与 PlaceholderAPI 集成的简化接口，用于创建自定义占位符
- 类型: 接口
- 所属模块: bukkit-hook

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> String.replacePlaceholder(player: Player): String -> 使用 PlaceholderAPI 替换字符串中的占位符
> List<String>.replacePlaceholder(player: Player): List<String> -> 使用 PlaceholderAPI 替换字符串列表中的占位符
> String.replacePlaceholder(player: OfflinePlayer): String -> 使用 PlaceholderAPI 替换字符串中的占位符（离线玩家版本）
> List<String>.replacePlaceholder(player: OfflinePlayer): List<String> -> 使用 PlaceholderAPI 替换字符串列表中的占位符（离线玩家版本）

### 类内可被访问字段
> identifier: String -> 占位符的唯一标识符
> enabled: Boolean -> 是否启用此占位符，默认为 true
> autoReload: Boolean -> 是否在占位符被卸载时自动重新注册，默认为 false

### 类方法
> onPlaceholderRequest(player: Player?, args: String): String -> 处理在线玩家的占位符请求
> onPlaceholderRequest(player: OfflinePlayer?, args: String): String -> 处理离线玩家的占位符请求

## 实现细节
- 通过 ClassVisitor 机制自动注册实现了 PlaceholderExpansion 接口的类
- 使用匿名内部类适配 TabooLib 的 PlaceholderExpansion 接口到 PlaceholderAPI 的原生接口
- 支持自动重载功能，可在占位符被卸载时自动重新注册
- 提供扩展函数简化占位符替换操作，并处理 PlaceholderAPI 不存在的情况
- 在 LifeCycle.ENABLE 生命周期阶段进行注册

## 使用场景
> 创建自定义占位符供其他插件使用
> 在插件中使用 PlaceholderAPI 的占位符替换文本
> 需要在配置文件、消息等地方支持占位符功能

## 注意事项
> 实现类必须有一个实例（单例或静态实例）
> 如果 enabled 返回 false，则不会注册此占位符
> 默认实现的 onPlaceholderRequest 方法会返回未实现的提示信息，应当重写这些方法
> 扩展函数会捕获 NoClassDefFoundError 异常，在 PlaceholderAPI 不存在时返回原始字符串

