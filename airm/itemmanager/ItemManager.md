# ItemManager

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.ItemManager
- 基本用途: 物品源管理器，负责注册、获取和使用各种物品源
- 类型: 具体类
- 所属模块: 物品管理工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> sources: ConcurrentHashMap<String, ItemSource> -> 存储已注册的物品源，键为物品源名称

### 类方法
> get(source: String): ItemSource? -> 根据名称获取物品源，使用操作符重载
> register(instance: ItemSource): Unit -> 注册一个物品源
> getSource(source: String): ItemSource -> 获取物品源，支持别名匹配，找不到时返回Minecraft源并记录警告
> parse2ItemStack(id: String, player: Player? = null): BuildSourceItem -> 解析物品ID字符串并构建物品

## 实现细节
- 使用ConcurrentHashMap存储物品源，支持线程安全的并发访问
- 在初始化时自动注册所有预定义的物品源，包括：
  - AzureFlow、CraftEngine、ItemsAdder、Minecraft
  - MMOItems、MythicMobs、NeigeItems、Oraxen
  - PxRpg、SXItem、Zaphkiel
- 注册物品源时检查是否已存在相同名称的物品源，避免重复注册
- 仅注册isLoaded为true的物品源，确保只有可用插件才被激活
- 支持通过物品源名称或别名查找物品源
- 当找不到指定物品源时，默认回退到Minecraft物品源
- 物品ID解析支持两种格式：
  1. "source:itemID"格式，如"minecraft:stone"
  2. 简单的"itemID"格式，此时默认使用"minecraft"作为源
- 在构建物品时捕获可能的异常，出错时回退到Minecraft物品源
- 返回BuildSourceItem对象，包含完整的物品构建信息

## 使用场景
> 作为插件的物品管理系统核心，统一管理多种物品来源
> 在命令系统中，解析玩家输入的物品ID字符串并获取实际物品
> 在配置文件中，使用统一的字符串格式引用不同来源的物品
> 允许插件开发者注册自定义物品源，扩展系统功能

## 注意事项
> 物品ID应使用"source:itemID"格式，否则默认为Minecraft物品
> 在物品解析过程中可能会发生异常，已内置异常处理
> 找不到匹配的物品源时会使用Minecraft作为默认源并记录警告
> 初始化时会自动尝试注册所有预定义的物品源，但只有对应插件加载时才会生效
> 使用线程安全容器，可在多线程环境中安全使用

## 使用实例
> 基本使用方法
```kotlin
val itemManager = ItemManager()
val player = // 获取玩家

// 解析并获取物品
val itemResult = itemManager.parse2ItemStack("mythicmobs:DragonSword", player)
val item = itemResult.itemStack

// 给予玩家
player.inventory.addItem(item)

// 获取物品来源信息
println("物品ID: ${itemResult.id}")
println("物品来源: ${itemResult.source}")
```

> 注册自定义物品源
```kotlin
class MyCustomSource : ItemSource {
    override val name: String get() = "mycustom"
    override val alias: List<String> get() = listOf("mc", "custom")
    override val pluginName: String get() = "MyCustomPlugin"
    override val isLoaded: Boolean get() = true // 或检查实际插件是否加载
    
    override fun build(id: String, player: Player?): ItemStack {
        // 自定义物品构建逻辑
        return ItemStack(Material.DIAMOND_SWORD) // 示例
    }
}

// 注册自定义源
val itemManager = ItemManager()
itemManager.register(MyCustomSource())

// 使用自定义源
val item = itemManager.parse2ItemStack("mycustom:special_item", player)
```

> 在命令处理中解析物品ID
```kotlin
fun handleGiveCommand(sender: Player, args: Array<String>) {
    if (args.isEmpty()) {
        sender.sendMessage("请指定物品ID")
        return
    }
    
    val itemManager = ItemManager() // 实际应用中应该使用单例或注入
    val itemId = args[0]
    
    try {
        val buildResult = itemManager.parse2ItemStack(itemId, sender)
        
        sender.inventory.addItem(buildResult.itemStack)
        sender.sendMessage("已给予物品: $itemId (来源: ${buildResult.source})")
    } catch (e: Exception) {
        sender.sendMessage("无法创建物品: $itemId")
    }
}
```

> 获取特定物品源
```kotlin
val itemManager = ItemManager()

// 直接通过名称获取
val mythicSource = itemManager["mythicmobs"]

// 或使用getSource方法，支持别名
val sameSource = itemManager.getSource("mm")

// 检查物品源是否可用
if (mythicSource != null && mythicSource.isLoaded) {
    // 使用特定物品源构建物品
    val mythicItem = mythicSource.build("DragonSword", player)
    player.inventory.addItem(mythicItem)
}
```