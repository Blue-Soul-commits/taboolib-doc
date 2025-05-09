# XEnchantment

## 基本信息
- 类名和包路径: taboolib.library.xseries.XEnchantment
- 基本用途: 提供对 Minecraft 附魔的跨版本支持，包含多种别名映射
- 类型: 枚举类
- 所属模块: platform-bukkit-impl

## 类结构

### 公开静态字段
> REGISTRY: XRegistry<XEnchantment, Enchantment> -> 附魔注册表，用于管理所有附魔映射
> AQUA_AFFINITY, BANE_OF_ARTHROPODS, BINDING_CURSE 等: XEnchantment -> 所有 Minecraft 附魔的枚举常量
> EFFECTIVE_SMITE_ENTITIES: Set<EntityType> -> 被亡灵杀手附魔有效的实体类型集合（已弃用）
> EFFECTIVE_BANE_OF_ARTHROPODS_ENTITIES: Set<EntityType> -> 被节肢杀手附魔有效的实体类型集合（已弃用）
> VALUES: XEnchantment[] -> 所有附魔的缓存数组（已弃用）

### 公开静态方法
> of(@NotNull Enchantment enchantment): XEnchantment -> 将 Bukkit 附魔转换为 XEnchantment
> of(@NotNull String enchantment): Optional<XEnchantment> -> 通过名称获取 XEnchantment
> values(): XEnchantment[] -> 获取所有附魔（已弃用，建议使用 REGISTRY.getValues()）
> isSmiteEffectiveAgainst(@Nullable EntityType type): boolean -> 检查亡灵杀手是否对指定实体类型有效（已弃用）
> isArthropodsEffectiveAgainst(@Nullable EntityType type): boolean -> 检查节肢杀手是否对指定实体类型有效（已弃用）
> matchXEnchantment(@NotNull String enchantment): Optional<XEnchantment> -> 通过名称匹配附魔（已弃用，使用 of(String) 代替）
> matchXEnchantment(@NotNull Enchantment enchantment): XEnchantment -> 通过 Bukkit 附魔匹配（已弃用，使用 of(Enchantment) 代替）

### 类内可被访问字段
> ISFLAT: boolean -> 是否为扁平化版本（1.13+）
> IS_SUPER_FLAT: boolean -> 是否为超扁平化版本（支持 Registry 类）
> USES_WRAPPER: boolean -> 是否使用 EnchantmentWrapper

### 类方法
> getBook(int level): ItemStack -> 获取指定等级的附魔书
> getEnchant(): Enchantment -> 获取原版附魔（已弃用，使用 get() 代替）
> friendlyName(): String -> 获取友好名称
> isSupported(): boolean -> 检查当前服务器是否支持此附魔
> or(XEnchantment other): XEnchantment -> 如果当前附魔不支持，则返回替代附魔

## 实现细节
- 使用 XRegistry 系统管理附魔映射，支持跨版本兼容
- 通过静态初始化块检测服务器版本特性（扁平化、超扁平化、包装器使用）
- 为每个附魔提供多个别名，方便从配置文件或命令中解析
- 处理 EnchantmentWrapper 和 CraftEnchantment 之间的映射关系
- 提供对已弃用的 EntityType 集合的向后兼容性支持

## 使用场景
> 从配置文件或用户输入中解析附魔名称
> 在不同 Minecraft 版本间提供一致的附魔 API
> 创建附魔书或为物品添加附魔
> 检查特定附魔对实体的有效性

## 注意事项
> 附魔等级从 1 开始，而不是从 0 开始
> 许多旧方法已被弃用，应使用新的 of() 方法和 REGISTRY 系统
> 对于实体类型检查，应使用 XTag 系统而不是已弃用的 EFFECTIVE_*_ENTITIES 集合

