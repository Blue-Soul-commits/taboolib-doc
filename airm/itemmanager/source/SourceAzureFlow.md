# SourceAzureFlow

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourceAzureFlow
- 基本用途: AzureFlow物品库的ItemSource接口实现，用于从AzureFlow插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"azureflow"
> alias: List<String> -> 物品库别名列表，包含"af"
> pluginName: String -> 物品库对应的插件名称，值为"AzureFlow"

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用AzureFlow API构建物品

## 实现细节
- 实现了ItemSource接口，提供从AzureFlow插件获取物品的能力
- 使用AzureFlowAPI.getFactory方法获取物品工厂
- 通过factory.build().virtualItemStack(player)构建虚拟物品堆
- 当物品ID不存在时，调用继承自接口的warnItemNotFound方法返回错误提示物品
- 支持提供玩家参数，可能用于处理特定于玩家的物品属性

## 使用场景
> 在物品管理系统中支持从AzureFlow插件获取物品
> 在命令或GUI界面中，允许玩家引用AzureFlow物品
> 在脚本或任务系统中，通过统一的物品源接口获取AzureFlow物品
> 在物品配方或掉落物系统中，指定使用AzureFlow物品

## 注意事项
> 使用前需确保服务器已安装并加载AzureFlow插件
> 可通过"azureflow"或简写"af"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于io.rokuko.azureflow.api.AzureFlowAPI，版本变更可能影响兼容性
