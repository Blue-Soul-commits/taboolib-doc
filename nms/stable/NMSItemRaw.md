# NMSItemRaw

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSItemRaw
- 基本用途: 提供将 Source 对象写入物品元数据的扩展函数
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> ItemMeta.setDisplayNameComponent(source: Source): ItemMeta -> 将 Source 写入物品的显示名称
> ItemMeta.setLoreComponents(source: List<Source>): ItemMeta -> 将 Source 列表写入物品的描述

### 类内可被访问字段
> 无

### 类方法
> 无（文件只包含扩展函数）

## 实现细节
- 使用 Kotlin 扩展函数为 `ItemMeta` 类添加功能
- 通过反射调用原生方法或设置私有字段来实现功能
- 对于 `setDisplayNameComponent`：
  - 首先尝试调用 `setDisplayNameComponent` 方法
  - 如果方法不存在，则直接设置 `displayName` 字段
- 对于 `setLoreComponents`：
  - 首先尝试调用 `setLoreComponents` 方法
  - 如果方法不存在，则直接设置 `lore` 字段
- 使用 `NMSMessage.instance.fromJson()` 将 JSON 格式的消息转换为 NMS 对象

## 使用场景
> 在需要设置物品的富文本显示名称时使用
> 在需要设置物品的富文本描述时使用
> 在支持聊天组件的插件中使用，如聊天、GUI 等

## 注意事项
> 仅支持 Minecraft 1.17 及以上版本，低版本会抛出 `UnsupportedVersionException`
> 需要依赖 `taboolib.module.chat.Source` 类来创建富文本内容
> 使用反射机制，可能会因为 Minecraft 版本更新导致方法或字段名变化而失效
> 在不同服务端实现（如 Paper、Spigot）中可能有不同的行为

