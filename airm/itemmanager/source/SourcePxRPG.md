# SourcePxRpg

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.source.SourcePxRpg
- 基本用途: PxRpg物品库的ItemSource接口实现，用于从PxRpg插件中获取物品
- 类型: 具体类(实现ItemSource接口)
- 所属模块: 物品管理工具模块 - 物品来源实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> name: String -> 物品库名称，值为"pxrpg"
> alias: List<String> -> 物品库别名列表，包含"pr"
> pluginName: String -> 物品库对应的插件名称，值为"PxRpg"
> manager: ItemManager -> PxRpg物品管理器，懒加载初始化

### 类方法
> build(id: String, player: Player?): ItemStack -> 使用PxRpg API构建物品

## 实现细节
- 实现了ItemSource接口，提供从PxRpg插件获取物品的能力
- 支持高级物品ID格式："物品ID,level=2;bind=已绑定"，可传递额外参数
- 使用懒加载方式初始化ItemManager，仅在首次使用时获取
- 通过Module.getModule获取PxRpg的ItemModule和对应ItemManager
- 使用ParameterResolver解析参数字符串，支持多个键值对参数
- 将Bukkit玩家转换为PxRpg玩家对象进行处理
- 最终将PxRpg物品对象转换回Bukkit的ItemStack返回
- 当物品ID不存在时，调用继承自接口的warnItemNotFound方法返回错误提示物品

## 使用场景
> 在物品管理系统中支持从PxRpg插件获取自定义物品
> 在命令或GUI界面中，允许玩家引用PxRpg物品，并可指定额外参数
> 在脚本或任务系统中，通过统一的物品源接口获取PxRpg物品
> 在物品配方或掉落物系统中，指定使用PxRpg物品，可以精确控制物品属性

## 注意事项
> 使用前需确保服务器已安装并加载PxRpg插件
> 物品ID支持高级格式，可以添加多个参数，例如："sword_01,level=5;quality=epic"
> 可通过"pxrpg"或简写"pr"引用该物品源
> 构建物品时可能会返回错误提示物品(基岩)，调用方需要进行检查
> 依赖于PxRpg的API，版本变更可能影响兼容性
> manager字段使用lateinit var延迟初始化，在首次build调用时才会初始化
