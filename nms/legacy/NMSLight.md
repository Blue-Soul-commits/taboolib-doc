# NMSLight

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSLight
- 基本用途: 提供 Minecraft 中光照操作的抽象接口和扩展函数
- 类型: 抽象类和扩展函数
- 所属模块: bukkit-nms-legacy

## 类结构

### 扩展函数
> Block.createLight(lightLevel: Int, lightType: LightType = LightType.ALL, update: Boolean = true, viewers: Collection<Player> = Bukkit.getOnlinePlayers()): Boolean -> 在方块位置创建光源
> Block.deleteLight(lightType: LightType = LightType.ALL, update: Boolean = true, viewers: Collection<Player> = Bukkit.getOnlinePlayers()): Boolean -> 删除方块位置的光源
> Block.updateLight(lightType: LightType, viewers: Collection<Player>) -> 更新方块位置的光照

### 抽象方法
> createLight(block: Block, lightType: LightType, lightLevel: Int): Boolean -> 创建光源
> deleteLight(block: Block, lightType: LightType): Boolean -> 删除光源
> getRawLightLevel(block: Block, lightType: LightType): Int -> 获取原始光照等级
> setRawLightLevel(block: Block, lightType: LightType, lightLevel: Int) -> 设置原始光照等级
> recalculateLight(block: Block, lightType: LightType) -> 重新计算光照
> recalculateLightAround(block: Block, lightType: LightType, lightLevel: Int) -> 重新计算周围的光照
> updateLight(chunk: Chunk, viewers: Collection<Player>) -> 更新区块的光照
> updateLightUniversal(block: Block, lightType: LightType, viewers: Collection<Player>) -> 通用方式更新方块的光照

## 实现细节
- 所有扩展函数都标记为 @Deprecated("停止维护")，表示不再维护
- 使用 nmsProxy<NMSLight>() 获取适合当前 Minecraft 版本的实现
- 在 Minecraft 1.12 以下版本抛出 UnsupportedVersionException
- 创建光源前会检查现有光照等级，如果高于要设置的等级，先删除现有光源
- 更新光照时根据 MinecraftVersion.isUniversal 选择不同的更新方式
- 非通用版本会更新方块所在区块及其周围 8 个区块的光照

## 使用场景
> 在游戏中创建自定义光源
> 删除已存在的光源
> 更新特定区域的光照
> 实现动态光照效果

## 注意事项
> 所有功能已标记为废弃，不再维护
> 仅支持 Minecraft 1.12 及以上版本
> 光照更新可能会影响游戏性能，特别是频繁更新时
> 光照更新仅对指定的玩家可见

## 使用实例

```kotlin
// 创建一个最大亮度的光源
block.createLight(
    lightLevel = 15,
    lightType = LightType.ALL,
    update = true
)

// 创建一个只有方块光照的光源
block.createLight(
    lightLevel = 10,
    lightType = LightType.BLOCK,
    update = true
)

// 删除光源
block.deleteLight(
    lightType = LightType.ALL,
    update = true
)

// 仅为特定玩家更新光照
val players = listOf(player1, player2)
block.createLight(
    lightLevel = 15,
    lightType = LightType.ALL,
    update = true,
    viewers = players
)

// 获取原始光照等级
val lightLevel = nmsProxy<NMSLight>().getRawLightLevel(block, LightType.BLOCK)
```