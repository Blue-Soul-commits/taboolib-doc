# SourceCraftEngine

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceCraftEngine
- 基本用途: CraftEngine物品库的ItemSource接口实现，用于从CraftEngine插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"craftengine"
> alias: List<String> -> 物品库别名列表，包含"ce"
> pluginName: String -> 物品库对应的插件名称，值为"CraftEngine"

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用CraftEngine API构建物品

## 实现细节
- 实现了ItemSource接口，提供从CraftEngine插件获取物品的能力
- 支持命名空间格式的物品ID，格式为"namespace:material"
- 使用String.split将ID分割为命名空间和材料ID两部分
- 使用BukkitCraftEngine.instance().adapt将Bukkit玩家转换为CraftEngine玩家对象
- 通过CraftEngineItems.byId方法和Key对象获取物品
- 调用item.buildItemStack构建最终的物品堆
- 当物品ID不存在时，调用继承自接口的warnItemNotFound方法返回错误提示物品

## 使用场景
> 在物品管理系统中支持从CraftEngine插件获取物品
> 在命令或GUI界面中，允许玩家引用CraftEngine物品
> 在脚本或任务系统中，通过统一的物品源接口获取CraftEngine物品
> 在物品配方或掉落物系统中，指定使用CraftEngine物品

## 注意事项
> 使用前需确保服务器已安装并加载CraftEngine插件
> 物品ID必须使用命名空间格式，如"minecraft:stone"，否则会抛出异常
> 可通过"craftengine"或简写"ce"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于CraftEngine的API，版本变更可能影响兼容性
