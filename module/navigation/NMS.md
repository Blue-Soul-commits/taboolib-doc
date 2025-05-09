# NMS
## 基本信息
- 类名和包路径: taboolib.module.navigation.NMS
- 基本用途: 提供跨版本 Minecraft 服务器实现的抽象接口，用于获取实体和方块的碰撞箱等信息
- 类型: 抽象类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> instance: NMS -> 当前服务器版本的 NMS 实现实例
> INSTANCE: NMS -> 已弃用的 instance 别名，保留用于向后兼容

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> getBoundingBox(entity: Entity): BoundingBox? -> 获取实体的碰撞箱
> getBoundingBox(block: Block): BoundingBox? -> 获取方块的碰撞箱
> getBlockHeight(block: Block): Double -> 获取方块的高度
> isDoorOpened(block: Block): Boolean -> 检查门方块是否处于打开状态

## 实现细节
- 使用 TabooLib 的 nmsProxy 系统自动生成适配当前服务器版本的实现类
- 提供抽象方法定义，具体实现由各版本的适配器提供
- 通过静态单例模式提供全局访问点
- 支持获取实体和方块的碰撞箱、方块高度和门状态等底层信息

## 使用场景
> 在寻路系统中获取实体和方块的碰撞箱信息
> 计算实体是否可以通过特定空间
> 判断门是否打开以决定寻路策略
> 获取方块的精确高度用于垂直移动计算

## 注意事项
> 使用 nmsProxy 生成的实现类，依赖于正确配置的 NMS 映射
> INSTANCE 字段已被弃用，应使用 instance 代替
> 返回的 BoundingBox 对象是 TabooLib 自定义的，而非 Bukkit 原生的
> 某些方法可能在特定版本的 Minecraft 上有不同行为，需要在使用时考虑兼容性
