# DefaultAttribute

## 基本信息
- 类名和包路径: taboolib.platform.util.DefaultAttribute
- 基本用途: 提供 Minecraft 原版装备的默认属性数值查询功能
- 类型: 工具类
- 所属模块: taboolib.platform.util

## 类结构

### 公开静态字段
> ATTACK_SPEED: HashMap<String, Double> -> 存储各类武器的攻击速度属性值
> ATTACK_DAMAGE: HashMap<String, Double> -> 存储各类武器的攻击伤害属性值
> ARMOR: HashMap<String, Double> -> 存储各类防具的护甲值
> ARMOR_TOUGHNESS: HashMap<String, Double> -> 存储各类防具的护甲韧性值
> KNOCKBACK_RESISTANCE: HashMap<String, Double> -> 存储各类防具的击退抗性值

### 公开静态方法
> getAttackDamage(type: Material): double -> 获取指定物品类型的攻击伤害属性值
> getAttackSpeed(type: Material): double -> 获取指定物品类型的攻击速度属性值
> getArmor(type: Material): double -> 获取指定物品类型的护甲值
> getArmorToughness(type: Material): double -> 获取指定物品类型的护甲韧性值
> getKnockbackResistance(type: Material): double -> 获取指定物品类型的击退抗性值
> getDefault(type: Material): Map<String, Double> -> 获取指定物品类型的所有默认属性值

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 使用静态初始化块预先填充所有原版装备的属性数据
- 对于某些类型的武器（如剑、铲、镐）使用通用属性值，通过后缀匹配进行判断
- 锄头的攻击伤害使用统一值，通过后缀"_HOE"匹配
- 返回值为0.0表示该物品没有对应属性
- getDefault方法只返回非零属性值，使用标准的属性名称格式（如"GENERIC_ATTACK_DAMAGE"）

## 使用场景
> 需要获取原版物品默认属性值的插件功能
> 创建自定义物品时参考原版属性值
> 计算装备属性总和时获取基础值
> 模拟原版属性系统时使用

## 注意事项
> 属性值与Minecraft版本相关，可能随游戏版本更新而变化
> 返回的属性名称使用Minecraft属性系统的标准格式（GENERIC_前缀）
> 对于不存在的物品类型或没有特定属性的物品，返回0.0而不是null
> 该类仅包含原版物品的属性数据，不包含模组或插件添加的物品
