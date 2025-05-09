# NMSPotionEffect

## 基本信息
- 类名和包路径: taboolib.module.nms.legacy.NMSPotionEffect
- 基本用途: 获取不同 Minecraft 版本中药水效果的语言文件节点
- 类型: 抽象类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> instance: NMSPotionEffect -> 通过 nmsProxy 懒加载的单例实例

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> getLanguageKey(potionEffectType: PotionEffectType): MinecraftLanguage.LanguageKey -> 获取药水效果的语言文件节点，例如 `effect.minecraft.regeneration`

## 实现细节
- 使用 `nmsProxy` 创建代理实例，实际实现类为 `NMSPotionEffectImpl`
- 通过 `unsafeLazy` 延迟初始化单例实例
- 实现类 `NMSPotionEffectImpl` 根据不同的 Minecraft 版本使用不同的方法获取药水效果的语言文件节点

## 使用场景
> 在需要获取药水效果的本地化名称时使用
> 在 NMSTranslate 类中被调用，用于获取药水效果的语言文件节点

## 注意事项
> 仅适用于 1.13 及以下版本的 Minecraft
> 在更高版本中，应使用 NMSTranslate 类中的相应方法
> 需要根据不同的 Minecraft 版本使用不同的 NMS 类，因此依赖于服务器版本

