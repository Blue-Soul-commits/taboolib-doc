# SourceMMOItems

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceMMOItems
- 基本用途: MMOItems物品库的ItemSource接口实现，用于从MMOItems插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"mmoitems"
> alias: List<String> -> 物品库别名列表，包含"mi"和"mmo"
> pluginName: String -> 物品库对应的插件名称，值为"MMOItems"

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用MMOItems API构建物品

## 实现细节
- 实现了ItemSource接口，提供从MMOItems插件获取物品的能力
- 物品ID格式为"类型,物品ID"，使用逗号分隔
- 使用String.split将ID分割为类型和物品ID两部分
- 通过Type.get方法获取MMOItems物品类型
- 使用MMOItems.plugin.getItem方法获取物品实例
- 当物品ID不存在时，调用继承自接口的warnItemNotFound方法返回错误提示物品
- 注意player参数在当前实现中未被使用，但保留以符合接口定义

## 使用场景
> 在物品管理系统中支持从MMOItems插件获取自定义物品
> 在命令或GUI界面中，允许玩家引用MMOItems物品
> 在脚本或任务系统中，通过统一的物品源接口获取MMOItems物品
> 在物品配方或掉落物系统中，指定使用MMOItems物品

## 注意事项
> 使用前需确保服务器已安装并加载MMOItems插件
> 物品ID必须使用特定格式："类型,物品ID"，例如"SWORD,fire_blade"
> 可通过"mmoitems"或简写"mi"或"mmo"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于MMOItems的API，版本变更可能影响兼容性
> 当前实现未使用player参数，可能会影响某些需要玩家上下文的MMOItems特性
