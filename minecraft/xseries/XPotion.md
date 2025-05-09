# XPotion
## 基本信息
- 类名和包路径: taboolib.library.xseries.XPotion
- 基本用途: 提供跨版本的药水效果类型支持，包含多种别名映射和实用工具方法
- 类型: 枚举类
- 所属模块: taboolib.library.xseries

## 类结构
### 公开静态字段
> VALUES: XPotion[] -> 缓存的XPotion.values()数组，避免重复调用values()方法分配内存
> DEBUFFS: Set<XPotion> -> 不可修改的"负面"药水效果集合（已弃用，建议使用XTag.DEBUFFS）
> REGISTRY: XRegistry<XPotion, PotionEffectType> -> XPotion的注册表，用于名称和Bukkit类型的映射

### 公开静态方法
> of(String potion): Optional<XPotion> -> 从字符串解析XPotion对象
> of(PotionType potion): XPotion -> 从PotionType获取对应的XPotion
> of(PotionEffectType type): XPotion -> 从PotionEffectType获取对应的XPotion
> parseEffect(String potion): Effect -> 从字符串解析药水效果，支持持续时间、等级和几率
> parseEffects(List<String> effectsString): List<Effect> -> 解析多个药水效果字符串
> addEffects(LivingEntity entity, List<String> effects): void -> 将多个药水效果应用到实体上
> throwPotion(LivingEntity entity, Color color, PotionEffect... effects): ThrownPotion -> 让实体投掷药水
> buildItemWithEffects(Material type, Color color, PotionEffect... effects): ItemStack -> 创建带有指定效果的药水物品
> canHaveEffects(Material material): boolean -> 检查材质是否可以拥有药水效果

### 类内可被访问字段
> potionEffectType: PotionEffectType -> 对应的Bukkit药水效果类型
> potionType: PotionType -> 对应的Bukkit药水类型

### 类方法
> getPotionEffectType(): PotionEffectType -> 获取对应的Bukkit药水效果类型
> getNames(): String[] -> 获取药水效果的名称数组
> get(): PotionEffectType -> 获取对应的Bukkit药水效果类型
> getPotionType(): PotionType -> 获取对应的Bukkit药水类型
> buildPotionEffect(int duration, int amplifier): PotionEffect -> 创建具有指定持续时间和等级的药水效果
> toString(): String -> 返回友好可读的字符串名称

## 实现细节
- 使用枚举实现，每个枚举值对应一个Minecraft药水效果类型
- 支持多种别名映射，使用EssentialsX的药水列表作为别名来源
- 通过XRegistry实现跨版本的名称和Bukkit类型映射
- 包含内部类Effect，用于处理带有几率的药水效果
- 支持从字符串配置解析药水效果，包括持续时间、等级和应用几率

## 使用场景
> 需要跨版本处理药水效果时，避免直接使用可能在不同版本中变化的Bukkit API
> 从配置文件中读取药水效果并应用到实体或物品上
> 创建自定义药水物品，如飞溅药水、滞留药水或药箭
> 需要通过字符串名称（包括别名）查找药水效果类型

## 注意事项
> 部分方法仅适用于Minecraft 1.9+版本
> 已弃用的方法（如matchXPotion）应使用其替代方法（如of）
> 药水效果的持续时间单位为tick（1秒=20tick）
> 药水效果的等级从1开始，而Bukkit API中的amplifier从0开始

