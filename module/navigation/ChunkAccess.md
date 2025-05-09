# ChunkAccess
## 基本信息
- 类名和包路径: taboolib.module.navigation.ChunkAccess
- 基本用途: 提供检查世界区块加载状态的抽象接口
- 类型: 抽象类
- 所属模块: bukkit-navigation

## 类结构
### 公开静态字段
> instance: ChunkAccess -> 默认实现的单例实例，使用 Bukkit API 检查区块加载状态

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> isChunkLoaded(world: World, chunkX: Int, chunkZ: Int): Boolean -> 检查指定世界中的区块是否已加载

## 实现细节
- 定义为抽象类，允许不同的实现方式
- 提供默认实现作为单例实例，直接调用 Bukkit API 的 isChunkLoaded 方法
- 使用匿名内部类实现默认实例，简化使用
- instance 变量可被重新赋值，允许替换默认实现

## 使用场景
> 在寻路系统中检查目标区域的区块是否已加载
> 在生成路径前验证路径所经过的区块是否可用
> 在实体 AI 中确保目标区域已加载再进行寻路计算
> 作为可扩展的接口，允许自定义区块加载检查逻辑

## 注意事项
> 默认实现直接依赖 Bukkit API，在非 Bukkit 环境下需要提供自定义实现
> instance 变量可被修改，使用时应注意线程安全问题
> 区块坐标使用区块索引（chunkX, chunkZ）而非方块坐标
