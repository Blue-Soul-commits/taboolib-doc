# NMSImpl
## 基本信息
- 类名和包路径: taboolib.module.navigation.NMSImpl
- 基本用途: 实现 NMS 抽象类，提供跨版本 Minecraft 服务器的底层功能访问
- 类型: 实现类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> version: Int -> 当前服务器的主要版本号
> majorLegacy: Int -> 当前服务器的版本 ID，用于精确版本判断

### 类方法
> getBoundingBox(entity: Entity): BoundingBox -> 获取实体的碰撞箱
> getBoundingBox(block: Block): BoundingBox -> 获取方块的碰撞箱
> getBlockHeight(block: Block): Double -> 获取方块的高度
> isDoorOpened(block: Block): Boolean -> 检查门方块是否处于打开状态

## 实现细节
- 实现 NMS 抽象类，提供跨版本兼容的具体实现
- 使用 MinecraftVersion 工具类判断当前服务器版本，根据不同版本提供不同的实现逻辑
- 针对 1.9.R2 到 1.21.R1 的多个 Minecraft 版本提供兼容实现
- 使用反射和直接 NMS 调用相结合的方式访问服务器内部 API
- 处理了 Minecraft 版本更新中的 API 变化，如类名、方法名和包路径的变更

## 使用场景
> 通过 NMS.instance 间接使用，不应直接实例化
> 在寻路系统中获取实体和方块的精确碰撞箱信息
> 在路径生成时考虑方块高度和门状态
> 在跨版本插件中提供一致的 NMS 访问接口

## 注意事项
> 直接依赖特定版本的 NMS 类，需要根据 Minecraft 版本更新进行维护
> 使用了大量版本判断和条件分支，确保在不同版本上的兼容性
> 某些实现使用反射调用，可能在未来版本中需要更新
> 代码中包含针对特定版本的硬编码引用，如 v1_12_R1、v1_14_R1 等
> 使用了 @Suppress 注解忽略一些警告，如代码重复和未使用变量

