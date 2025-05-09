# ItemBuilder

## 基本信息
- 类名和包路径: taboolib.platform.util.ItemBuilder
- 基本用途: 提供流畅的API来创建和修改Bukkit物品
- 类型: Kotlin类和扩展函数
- 所属模块: bukkit-util

## 类结构

### 公开静态方法
> buildItem(itemStack: ItemStack, builder: ItemBuilder.() -> Unit = {}): ItemStack -> 通过现有物品构建新的物品
> buildItem(material: XMaterial, builder: ItemBuilder.() -> Unit = {}): ItemStack -> 通过XMaterial材质构建新的物品
> buildItem(material: Material, builder: ItemBuilder.() -> Unit = {}): ItemStack -> 通过Material材质构建新的物品

### 类内可被访问字段
> material: Material -> 物品材质
> amount: Int -> 数量
> damage: Int -> 附加值（损伤值）
> name: String? -> 展示名称
> lore: ArrayList<String> -> 描述
> flags: ArrayList<ItemFlag> -> 标签
> enchants: HashMap<Enchantment, Int> -> 附魔
> patterns: ArrayList<Pattern> -> 旗帜花纹
> color: Color? -> 颜色
> potions: ArrayList<PotionEffect> -> 药水效果
> potionData: PotionData? -> 基础药水效果
> spawnType: EntityType? -> 生物类型
> skullOwner: String? -> 头颅信息
> skullTexture: SkullTexture? -> 头颅材质信息
> isUnbreakable: Boolean -> 无法破坏
> customModelData: Int -> CustomModelData
> tooltipStyle: NamespacedKey? -> Tooltip样式(1.21.2+)
> itemModel: NamespacedKey? -> 物品模型(1.21.4+)
> unique: Boolean -> 唯一化
> originMeta: ItemMeta? -> 原始数据
> finishing: (ItemStack) -> Unit -> 构建完成时的最后修改

### 类方法
> setMaterial(material: XMaterial): Unit -> 设置材质
> shiny(): Unit -> 使物品发光
> hideAll(): Unit -> 隐藏所有附加信息
> unique(): Unit -> 唯一化物品
> colored(): Unit -> 对名称和描述进行颜色处理
> build(): ItemStack -> 构建物品

## 实现细节
- 支持从现有物品、Material或XMaterial创建新物品
- 提供流畅的DSL风格API来修改物品属性
- 自动处理不同版本Minecraft的兼容性问题
- 支持特殊物品类型如附魔书、皮革装备、药水、头颅等
- 通过try-catch块处理不同Minecraft版本的API差异
- 使用反射访问某些不直接暴露的属性或方法

## 使用场景
> 创建自定义物品时
> 修改现有物品的属性时
> 需要处理跨版本兼容性的物品创建时
> 创建特殊类型物品如自定义头颅、药水等

## 注意事项
> 某些功能在低版本Minecraft中不可用
> 头颅材质功能依赖"bukkit-xseries-skull"模块
> 使用反射的部分可能在未来版本中需要更新
> 对于空气类型的物品会抛出IllegalArgumentException异常

