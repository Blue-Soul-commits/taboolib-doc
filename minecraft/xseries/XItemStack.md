# XItemStack
## 基本信息
- 类名和包路径: taboolib.library.xseries.XItemStack
- 基本用途: YAML物品序列化与反序列化工具，支持跨版本物品操作
- 类型: 工具类
- 所属模块: platform-bukkit-impl

## 类结构
### 公开静态字段
> SUPPORTS_CUSTOM_MODEL_DATA: boolean -> 是否支持自定义模型数据
> SUPPORTS_POTION_COLOR: boolean -> 是否支持药水颜色
> SUPPORTS_Inventory_getStorageContents: boolean -> 是否支持获取库存内容

### 公开静态方法
> serialize(item: ItemStack, config: ConfigurationSection): void -> 将物品序列化到配置节点
> serialize(item: ItemStack, config: ConfigurationSection, translator: Function<String, String>): void -> 将物品序列化到配置节点，并应用文本转换器
> serialize(item: ItemStack): Map<String, Object> -> 将物品序列化为Map
> deserialize(config: ConfigurationSection): ItemStack -> 从配置节点反序列化物品
> deserialize(serializedItem: Map<String, Object>): ItemStack -> 从Map反序列化物品
> deserialize(config: ConfigurationSection, translator: Function<String, String>): ItemStack -> 从配置节点反序列化物品，并应用文本转换器
> deserialize(config: ConfigurationSection, translator: Function<String, String>, restart: Consumer<Exception>): ItemStack -> 从配置节点反序列化物品，并处理异常
> deserialize(serializedItem: Map<String, Object>, translator: Function<String, String>): ItemStack -> 从Map反序列化物品，并应用文本转换器
> edit(item: ItemStack, config: ConfigurationSection, translator: Function<String, String>, restart: Consumer<Exception>): ItemStack -> 根据配置编辑物品
> parseColor(str: String): Color -> 解析RGB颜色字符串
> giveOrDrop(player: Player, items: ItemStack...): List<ItemStack> -> 给予玩家物品，无法放入背包的物品会掉落
> giveOrDrop(player: Player, split: boolean, items: ItemStack...): List<ItemStack> -> 给予玩家物品，可控制是否拆分堆叠
> addItems(inventory: Inventory, split: boolean, items: ItemStack...): List<ItemStack> -> 向物品栏添加物品
> addItems(inventory: Inventory, split: boolean, modifiableSlots: Predicate<Integer>, items: ItemStack...): List<ItemStack> -> 向物品栏添加物品，可指定可修改的槽位
> firstPartial(inventory: Inventory, item: ItemStack, beginIndex: int): int -> 查找第一个可堆叠的物品槽位
> firstPartial(inventory: Inventory, item: ItemStack, beginIndex: int, modifiableSlots: Predicate<Integer>): int -> 查找第一个可堆叠的物品槽位，可指定可修改的槽位
> stack(items: Collection<ItemStack>): List<ItemStack> -> 堆叠物品集合
> stack(items: Collection<ItemStack>, similarity: BiPredicate<ItemStack, ItemStack>): List<ItemStack> -> 堆叠物品集合，可自定义相似度判断
> firstEmpty(inventory: Inventory, beginIndex: int): int -> 查找第一个空槽位
> firstEmpty(inventory: Inventory, beginIndex: int, modifiableSlots: Predicate<Integer>): int -> 查找第一个空槽位，可指定可修改的槽位
> firstPartialOrEmpty(inventory: Inventory, item: ItemStack, beginIndex: int): int -> 查找第一个空槽位或可堆叠的物品槽位
> getStorageContents(inventory: Inventory): ItemStack[] -> 获取物品栏存储内容
> notEmpty(item: ItemStack): boolean -> 检查物品是否非空
> isEmpty(item: ItemStack): boolean -> 检查物品是否为空

### 类内可被访问字段
> DEFAULT_MATERIAL: XMaterial -> 默认材质，用于处理空气物品

### 类方法
> 无公开实例方法（工具类）

## 实现细节
- 使用静态初始化块检测当前服务器版本支持的特性
- 通过反射检测不同版本的Bukkit API支持情况
- 支持跨版本物品序列化与反序列化
- 支持各种特殊物品类型（如附魔书、药水、盔甲等）
- 提供异常处理机制处理未知材质或不支持的材质
- 支持物品属性、附魔、标志等高级特性

## 使用场景
> 配置文件中保存和加载物品
> 跨版本物品数据转换
> 物品栏管理和操作
> 物品序列化为字符串或Map用于数据库存储
> GUI菜单创建和管理

## 注意事项
> 不同Minecraft版本的物品格式有差异，使用时需注意版本兼容性
> 序列化特殊物品（如头颅）可能需要额外处理
> 使用deserialize时，如果配置中的材质不存在，会抛出UnknownMaterialCondition异常
> 使用edit方法时可以提供restart参数处理异常情况

