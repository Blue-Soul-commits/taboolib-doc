# NMSToast

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSToast
- 基本用途: 提供在 Minecraft 中发送虚拟成就提示（Toast）的功能
- 类型: 扩展函数和工具函数
- 所属模块: bukkit-nms-legacy

## 类结构

### 扩展函数
> Player.sendToast(icon: Material, message: String, frame: ToastFrame = ToastFrame.TASK, background: ToastBackground = ToastBackground.ADVENTURE) -> 向玩家发送虚拟成就提示（已废弃）

### 私有函数
> awardAdvancement(player: Player, key: NamespacedKey) -> 赋予玩家成就
> revokeAdvancement(player: Player, key: NamespacedKey) -> 注销玩家成就
> injectAdvancement(key: NamespacedKey, toast: JsonObject): NamespacedKey -> 将成就注入到服务器
> unwrap(newAdvancements: Any): MutableMap<Any, Any> -> 将新的 ImmutableMap 写入 AdvancementDataWorld（1.20.2+）
> ejectAdvancement(key: NamespacedKey): NamespacedKey -> 注销成就
> toJsonToast(icon: String, title: String, frame: ToastFrame, background: ToastBackground, customModelData: Int = 0): JsonObject -> 生成成就 Json

### 私有属性
> toastMap: ConcurrentHashMap<Toast, NamespacedKey> -> 缓存 Toast 对象和对应的 NamespacedKey
> classJsonElement: Class<*> -> JsonElement 类
> classCraftNamespacedKey: Class<*> -> CraftNamespacedKey 类
> classMinecraftServer: Class<*> -> MinecraftServer 类
> classAdvancement: Class<*> -> Advancement 类
> classSerializedAdvancement: Class<*> -> SerializedAdvancement 类
> constructorLootDeserializationContext: Constructor<*> -> LootDeserializationContext 构造函数
> lootDataManager: Any -> 根据版本获取的 LootData 管理器
> advancements: Any -> 根据版本获取的成就数据
> constructorAdvancementHolder: Constructor<*> -> AdvancementHolder 构造函数
> advancementsMap: MutableMap<Any, Any> -> 成就映射表

## 实现细节
- 使用 @Deprecated("停止维护") 标记所有公开函数，表示不再维护
- 在 Minecraft 1.20.2 及以上版本中，sendToast 方法不再可用
- 在 Minecraft 1.13 以下版本中，抛出 UnsupportedVersionException
- 使用 ConcurrentHashMap 缓存已创建的 Toast 对象，避免重复创建
- 通过反射获取和操作 NMS 类和对象
- 根据不同的 Minecraft 版本使用不同的方法获取和操作成就数据
- 使用 submit 函数在主线程上执行操作
- 使用延迟任务（delay = 20）在显示成就后注销成就

## 使用场景
> 向玩家发送自定义成就提示
> 创建临时的虚拟成就
> 实现游戏内通知系统
> 提供视觉反馈

## 注意事项
> 所有功能已标记为废弃，不再维护
> 在 Minecraft 1.20.2 及以上版本中不可用
> 仅支持 Minecraft 1.13 及以上版本
> 使用了大量反射操作，可能在未来版本中不稳定
> 成就注册和注销操作在主线程上执行，可能影响性能

