# BukkitTellrawJson

## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitTellrawJson
- 基本用途: 提供在聊天组件中显示物品悬浮提示的工具函数
- 类型: Kotlin 文件（包含扩展函数和工具函数）
- 所属模块: bukkit-nms-tag

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法（文件中只包含扩展函数）

### 类内可被访问字段
> classNMSItem: Class<*> -> 通过反射获取的 NMS Item 类

### 类方法
> ItemStack.toNMSKeyAndItemData(): Pair<String, String> -> 将物品转换为 NMS 键和物品数据的键值对
> ComponentText.hoverItem(itemStack: ItemStack): ComponentText -> 为组件文本添加物品悬浮提示
> RawMessage.hoverItem(itemStack: ItemStack): RawMessage -> 为原始消息添加物品悬浮提示
> nmsClassLegacy(name: String): Class<*> -> 获取指定名称的 NMS 类

## 实现细节
- 使用 NMSItemTag 获取物品的 NMS 副本和 JSON 数据
- 通过反射获取物品的注册表键（Registry Key）
- 对不同 Minecraft 版本提供兼容性支持：
  - 在高版本（1.13+）中使用 Material.key 获取物品键
  - 在低版本中通过反射获取物品键
- 将获取的键和 JSON 数据组合成对，用于在聊天组件中显示物品悬浮提示

## 使用场景
> 在聊天消息中添加可悬浮查看的物品提示
> 在 GUI 界面的文本组件中添加物品预览功能
> 在书本、告示牌等可交互文本中添加物品展示

## 注意事项
> 该实现包含对旧版本 Minecraft（1.12 及以下）的兼容性处理
> 代码中包含已注释的错误实现，作为历史参考（#359 问题）
> 依赖于 NMSItemTag 提供的跨版本 NBT 操作功能
> 使用反射获取 NMS 类和方法，可能在未来版本中需要更新
