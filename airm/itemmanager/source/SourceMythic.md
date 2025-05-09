# SourceMythic

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceMythic
- 基本用途: MythicMobs物品库的ItemSource接口实现，用于从MythicMobs插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"mythicmobs"
> alias: List<String> -> 物品库别名列表，包含"mm"和"mythic"
> pluginName: String -> 物品库对应的插件名称，值为"MythicMobs"

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用MythicMobs API构建物品

## 实现细节
- 实现了ItemSource接口，提供从MythicMobs插件获取物品的能力
- 使用ink.ptms.um.Mythic.API.getItemStack方法获取MythicMobs物品
- 当物品ID不存在时，调用继承自接口的warnItemNotFound方法返回错误提示物品
- 实现非常简洁，直接调用MythicMobs API并处理null返回值
- 支持玩家参数，可能影响物品的某些属性或变量替换

## 使用场景
> 在物品管理系统中支持从MythicMobs插件获取自定义物品
> 在命令或GUI界面中，允许玩家引用MythicMobs物品
> 在脚本或任务系统中，通过统一的物品源接口获取MythicMobs物品
> 在物品配方或掉落物系统中，指定使用MythicMobs物品

## 注意事项
> 使用前需确保服务器已安装并加载MythicMobs插件
> 可通过"mythicmobs"或简写"mm"或"mythic"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于ink.ptms.um.Mythic API，可能是TabooLib的MythicMobs集成，版本变更可能影响兼容性
