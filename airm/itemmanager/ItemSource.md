# ItemSource

## 基本信息
- 类名和包路径: top.maplex.arim.tools.itemmanager.ItemSource
- 基本用途: 定义物品来源接口，用于从不同物品库中构建物品
- 类型: 接口(interface)
- 所属模块: 物品管理工具模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> getPluginLoaded(pluginName: String): Boolean -> 检查指定名称的插件是否已加载

### 类内可被访问字段
> name: String -> 物品库名称，纯小写
> alias: List<String> -> 物品库别名列表
> pluginName: String -> 物品库对应的插件名称
> isLoaded: Boolean -> 物品库对应的插件是否已加载，默认实现为检查插件是否存在

### 类方法
> build(id: String, player: Player? = null): ItemStack -> 根据ID和玩家构建物品
> warnItemNotFound(value: String): ItemStack -> 当物品ID不存在时返回默认错误物品并记录日志

## 实现细节
- 定义了物品来源的标准接口，用于从不同物品库获取物品
- 提供了默认的isLoaded实现，基于插件名称检查
- 包含默认的warnItemNotFound实现，返回基岩方块并记录错误信息
- 使用companion object提供静态工具方法getPluginLoaded
- 设计为可扩展架构，允许通过实现该接口支持不同的物品库
- 支持物品库别名系统，增强用户体验
- 在注释中提供了实现示例，展示了集成第三方插件的方式

## 使用场景
> 作为插件扩展点，支持从各种物品库(如MythicMobs)获取物品
> 在物品管理系统中统一不同来源物品的获取接口
> 作为物品命令系统的底层支持，允许通过指定来源和ID获取物品
> 在物品脚本或配置系统中，使用统一格式引用不同来源的物品

## 注意事项
> 实现类需要提供特定物品库的构建逻辑
> name属性应该使用纯小写，便于匹配
> 物品构建可能会失败，实现类应处理异常情况
> player参数为可选，但某些物品库可能需要玩家上下文
> 根据注释示例，需要在启动时通过API注册实现类