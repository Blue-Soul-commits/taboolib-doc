# SourceOraxen

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceOraxen
- 基本用途: Oraxen物品库的ItemSource接口实现，用于从Oraxen插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"oraxen"
> alias: List<String> -> 物品库别名列表，包含"ox"
> pluginName: String -> 物品库对应的插件名称，值为"Oraxen"

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用Oraxen API构建物品

## 实现细节
- 实现了ItemSource接口，提供从Oraxen插件获取物品的能力
- 使用io.th0rgal.oraxen.api.OraxenItems.getItemById方法获取物品模型
- 调用oraxenItem.build()方法构建最终物品堆
- 当物品ID不存在时，调用继承自接口的warnItemNotFound方法返回错误提示物品
- 实现简洁明了，直接使用Oraxen的API获取物品
- 注意player参数在当前实现中未被直接使用，但保留以符合接口定义

## 使用场景
> 在物品管理系统中支持从Oraxen插件获取自定义物品
> 在命令或GUI界面中，允许玩家引用Oraxen物品
> 在脚本或任务系统中，通过统一的物品源接口获取Oraxen物品
> 在物品配方或掉落物系统中，指定使用Oraxen物品

## 注意事项
> 使用前需确保服务器已安装并加载Oraxen插件
> 可通过"oraxen"或简写"ox"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于io.th0rgal.oraxen.api.OraxenItems类，版本变更可能影响兼容性
> 当前实现中player参数传递给了virtualItemStack方法，但未对构建结果产生影响
