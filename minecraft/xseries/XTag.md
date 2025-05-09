# XTag
## 基本信息
- 类名和包路径: taboolib.library.xseries.XTag
- 基本用途: 用于将各种元素（如材料、附魔、实体类型等）按照共同特征分组，提供标签系统
- 类型: 泛型工具类
- 所属模块: TabooLib XSeries 库

## 类结构
### 公开静态字段
> AIR: XTag<XMaterial> -> 表示空气方块的标签
> INVENTORY_NOT_DISPLAYABLE: XTag<XMaterial> -> 表示不能在物品栏中显示的方块
> LOGS: XTag<XMaterial> -> 表示所有原木变体
> PLANKS: XTag<XMaterial> -> 表示所有木板类型
> WOODEN_DOORS: XTag<XMaterial> -> 表示所有木门
> WOODEN_TRAPDOORS: XTag<XMaterial> -> 表示所有木活板门
> FLUID: XTag<XMaterial> -> 表示纯流体（水和岩浆）
> DANGEROUS_BLOCKS: XTag<XMaterial> -> 表示可能伤害玩家的方块
> EFFECTIVE_SMITE_ENTITIES: XTag<XEntityType> -> 表示亡灵杀手附魔有效的实体类型
> EFFECTIVE_BANE_OF_ARTHROPODS_ENTITIES: XTag<XEntityType> -> 表示节肢杀手附魔有效的实体类型
> DEBUFFS: XTag<XPotion> -> 表示负面药水效果的集合

### 公开静态方法
> stringMatcher(elements: Collection<String>): List<Matcher<E>> -> 编译字符串匹配器列表，用于配置文件
> stringMatcher(elements: Collection<String>, errors: Collection<Matcher.Error>): List<Matcher<E>> -> 带错误收集的字符串匹配器编译
> anyMatchString(target: T, matchers: Collection<String>): boolean -> 检查目标是否匹配任何字符串匹配器
> anyMatch(target: T, matchers: Collection<Matcher<T>>): boolean -> 检查目标是否匹配任何匹配器
> isItem(material: XMaterial): boolean -> 检查材料是否为可获取的物品
> isInteractable(material: XMaterial): boolean -> 检查材料是否可交互
> getTag(name: String): Optional<XTag<?>> -> 通过名称获取标签

### 类内可被访问字段
> values: Set<T> -> 标签包含的所有值的集合

### 类方法
> isTagged(value: T): boolean -> 检查值是否被此标签标记
> getValues(): Set<T> -> 获取标签包含的所有值
> without(without: T...): XTag<T> -> 返回不包含指定值的新标签

## 实现细节
- 使用泛型支持多种类型的标签系统（XMaterial、XEnchantment、XEntityType等）
- 通过静态初始化块定义各种标签组合
- 使用TagBuilder内部类构建标签，支持继承其他标签的值
- 提供字符串匹配系统，支持精确匹配、包含匹配和正则表达式匹配
- 自动注册所有标签到TAGS映射中，支持通过名称查找
- 提供版本兼容性方法，如isItem和isInteractable，支持1.13前后的Minecraft版本

## 使用场景
> 检查材料是否属于特定类别（如木门、原木等）
> 配置文件中使用字符串匹配器过滤特定物品
> 检查实体是否受特定附魔影响
> 判断方块是否可交互或可作为物品获取
> 获取特定类别的所有材料（如所有羊毛、所有床等）

## 注意事项
> 该类内存占用较大，不应在不需要时初始化
> 建议在启动时初始化，以避免游戏中出现卡顿
> 字符串匹配中，应尽量使用CONTAINS标签而非REGEX标签以提高性能
> 某些方法（如isInteractable和isItem）在不同Minecraft版本中有不同实现

