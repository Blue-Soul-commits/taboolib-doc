# NMSTranslate

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSTranslate
- 基本用途: 提供跨版本的 Minecraft 本地化翻译功能
- 类型: 抽象类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> instance: NMSTranslate -> 通过 nmsProxy 懒加载的单例实例

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> getKey(itemStack: ItemStack): String -> 获取物品的键名，例如 "diamond_sword"
> getLanguageKey(itemStack: ItemStack): MinecraftLanguage.LanguageKey -> 获取物品的语言文件节点
> getLanguageKey(enchantment: Enchantment): MinecraftLanguage.LanguageKey -> 获取附魔的语言文件节点
> getLanguageKey(potionEffectType: PotionEffectType?): MinecraftLanguage.LanguageKey -> 获取药水效果的语言文件节点

## 实现细节
- 使用 `nmsProxy<NMSTranslate>()` 创建代理实例，实际实现类为 `NMSTranslateImpl`
- 通过 `unsafeLazy` 延迟初始化单例实例
- 提供多个扩展函数简化使用：
  - `ItemStack.getName()`: 获取物品的名称（优先显示名称，其次译名）
  - `Material.getI18nName()`: 获取材质的译名
  - `XMaterial.getI18nName()`: 获取 XMaterial 的译名
  - `ItemStack.getI18nName()`: 获取物品的译名
  - `Entity.getDisplayName()`: 获取实体的显示名称
  - `Entity.getI18nName()`: 获取实体的译名
  - `Enchantment.getI18nName()`: 获取附魔的译名
  - `PotionEffectType.getI18nName()`: 获取药水效果的译名
  - `ItemStack.getKey()`: 获取物品的键名
  - `ItemStack.getLanguageKey()`: 获取物品的语言文件节点
  - `Enchantment.getLanguageKey()`: 获取附魔的语言文件节点
  - `PotionEffectType.getLanguageKey()`: 获取药水效果的语言文件节点
- 使用 `translate` HashMap 缓存已翻译的名称，提高性能
- 实现类 `NMSTranslateImpl` 根据不同的 Minecraft 版本使用不同的方法获取译名
- 支持从 1.8 到 1.21 版本的 Minecraft
- 特别处理了 1.12 及以下版本的特殊物品，如药水和刷怪蛋
- 在 1.19.3+ 版本中，使用 Translatable 接口获取译名

## 使用场景
> 在需要获取物品、实体、附魔或药水效果的本地化名称时使用
> 在需要显示用户友好的名称时使用
> 在插件开发中需要跨版本兼容时使用
> 在需要支持多语言的插件中使用

## 注意事项
> 不同版本的 Minecraft 对本地化的处理方式不同
> 在 1.12 及以下版本，特殊物品（如药水和刷怪蛋）的处理较为复杂
> 在 1.19.3+ 版本中，可以使用 Translatable 接口简化获取译名的过程
> 使用反射机制获取 NMS 类和方法，可能会因为 Minecraft 版本更新导致方法或字段名变化而失效
> 在 1.12 及以下版本，不建议直接使用 `Material.getI18nName()`

