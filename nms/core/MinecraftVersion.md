# MinecraftVersion

## 基本信息
- 类名和包路径: taboolib.module.nms.MinecraftVersion
- 基本用途: 提供 Minecraft 版本检测和兼容性管理的工具类
- 类型: 单例对象
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> V1_8 到 V1_21: Int -> 表示各个主要 Minecraft 版本的常量值

### 公开静态方法
> isHigher(version: Int): Boolean -> 检查当前版本是否高于指定版本
> isHigherOrEqual(version: Int): Boolean -> 检查当前版本是否高于或等于指定版本
> isLower(version: Int): Boolean -> 检查当前版本是否低于指定版本
> isLowerOrEqual(version: Int): Boolean -> 检查当前版本是否低于或等于指定版本
> isIn(range: IntRange): Boolean -> 检查当前版本是否在指定范围内
> isIn(min: Int, max: Int): Boolean -> 检查当前版本是否在指定范围内
> isEqual(version: Int): Boolean -> 检查当前版本是否等于指定版本

### 类内可被访问字段
> minecraftVersion: String -> 当前运行的 Minecraft 版本（字符格式，如 v1_8_R3）
> runningVersion: String -> 当前运行的 Minecraft 版本（数字格式，如 1.8.8）
> isUniversalCraftBukkit: Boolean -> 是否为 universal obc 版本（Paper 1.20.6+）
> supportedVersion: Array<Array<String>> -> 所有受支持的 Minecraft 版本列表
> versionId: Int -> 版本 ID，使用 TabooLib 格式（如 1.8.8 -> 10808）
> majorLegacy: Int -> 版本 ID 的别名（已废弃）
> major: Int -> 主版本号（对应 V1_X 常量）
> minor: Int -> 次版本号
> isSupported: Boolean -> 是否支持当前运行版本
> isSkipped: Boolean -> 是否运行在一个被跳过的版本
> isUniversal: Boolean -> 是否为 1.17 以上版本
> isBundlePacketSupported: Boolean -> 是否支持 BundlePacket 数据包（1.19.4+）
> spigotMapping: Mapping -> 当前运行版本的 Spigot 映射文件
> paperMapping: Mapping -> 当前运行版本的 Paper 映射文件

## 实现细节
- 使用 @Inject 和 @PlatformSide 注解标记为 Bukkit 平台的注入对象
- 通过 unsafeLazy 延迟初始化各种版本信息
- 支持检测当前 Minecraft 版本并提供多种版本比较方法
- 管理 Spigot 和 Paper 的映射文件，用于 NMS 代码的反混淆
- 在初始化时检查版本兼容性，并在不兼容时发出警告或禁用插件
- 注册适当的 Reflex 重定向实现，用于处理不同环境下的反射操作

## 使用场景
> 检测当前 Minecraft 版本并根据版本执行不同的代码路径
> 管理插件对不同 Minecraft 版本的兼容性
> 提供 NMS 代码反混淆所需的映射文件
> 在不兼容的版本上提供友好的错误信息

## 注意事项
> 某些版本被标记为跳过（以 ! 开头），通常是因为 Mojang 发布了紧急修复版本
> 从 1.20.5 开始，Paper 进行了破坏性修改，影响了版本检测和 NMS 访问
> 在 Paper 1.20.6+ 环境中，minecraftVersion 方法会返回 "UNKNOWN"
> 在非开发模式下，如果当前版本不受支持，插件会被禁用