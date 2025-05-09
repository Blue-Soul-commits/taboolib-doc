# SourceItemsAdder

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceItemsAdder
- 基本用途: ItemsAdder物品库的ItemSource接口实现，用于从ItemsAdder插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"itemsadder"
> alias: List<String> -> 物品库别名列表，包含"ia"
> pluginName: String -> 物品库对应的插件名称，值为"ItemsAdder"

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用ItemsAdder API构建物品

## 实现细节
- 实现了ItemSource接口，提供从ItemsAdder插件获取物品的能力
- 使用dev.lone.itemsadder.api.CustomStack.getInstance方法获取自定义物品
- 通过调用customStack.itemStack获取Bukkit物品堆
- 当物品ID不存在时，调用继承自接口的warnItemNotFound方法返回错误提示物品
- 实现简洁明了，直接使用ItemsAdder的API获取物品
- 注意player参数在当前实现中未被使用，但保留以符合接口定义

## 使用场景
> 在物品管理系统中支持从ItemsAdder插件获取自定义物品
> 在命令或GUI界面中，允许玩家引用ItemsAdder物品
> 在脚本或任务系统中，通过统一的物品源接口获取ItemsAdder物品
> 在物品配方或掉落物系统中，指定使用ItemsAdder物品

## 注意事项
> 使用前需确保服务器已安装并加载ItemsAdder插件
> 可通过"itemsadder"或简写"ia"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于dev.lone.itemsadder.api.CustomStack类，版本变更可能影响兼容性
> 与其他物品源实现不同，当前实现未使用player参数，这可能会影响某些需要玩家上下文的功能
