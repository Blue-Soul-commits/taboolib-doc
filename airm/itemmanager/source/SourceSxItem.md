# SourceSXItem

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceSXItem
- 基本用途: SX-Item物品库的ItemSource接口实现，用于从SX-Item插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"sxitem"
> alias: List<String> -> 物品库别名列表，包含"sx"、"sx-item"和"si"
> pluginName: String -> 物品库对应的插件名称，值为"SX-Item"

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用SX-Item API构建物品

## 实现细节
- 实现了ItemSource接口，提供从SX-Item插件获取物品的能力
- 支持特殊的ID格式："物品ID:参数1:参数2:参数3..."，使用冒号分隔参数
- 使用String.split分割物品ID和参数
- 将第一个部分作为SX-Item的物品ID，后续部分作为额外参数
- 将参数列表转换为数组，使用展开运算符(*)传递给SX-Item API
- 依赖玩家对象，如果player为null则调用warnItemNotFound方法返回错误提示物品
- SX-Item的getItem方法将返回基于玩家和参数的定制物品

## 使用场景
> 在物品管理系统中支持从SX-Item插件获取自定义物品
> 在命令或GUI界面中，允许玩家引用SX-Item物品，并可指定额外参数
> 在脚本或任务系统中，通过统一的物品源接口获取SX-Item物品
> 在物品配方或掉落物系统中，指定使用SX-Item物品，可以精确控制物品属性

## 注意事项
> 使用前需确保服务器已安装并加载SX-Item插件
> 物品ID必须使用特定格式，使用冒号分隔参数，例如："sword:param1:param2"
> 需要有效的player参数，否则会返回错误提示物品
> 可通过"sxitem"或简写"sx"、"sx-item"、"si"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于github.saukiya.sxitem.SXItem类的API，版本变更可能影响兼容性
