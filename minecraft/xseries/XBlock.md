# XBlock

## 基本信息
- 类名和包路径: taboolib.library.xseries.XBlock
- 基本用途: 提供跨版本的方块操作工具，支持新旧版本 Minecraft 的 MaterialData/BlockData API
- 类型: 工具类
- 所属模块: platform-bukkit-impl

## 类结构

### 公开静态字段
> CROPS: Set<XMaterial> -> 包含所有作物类型的不可变集合（已弃用，建议使用 XTag.CROPS）
> DANGEROUS: Set<XMaterial> -> 包含所有危险方块类型的不可变集合（已弃用，建议使用 XTag.DANGEROUS_BLOCKS）
> CAKE_SLICES: byte -> 蛋糕的最大切片数量，值为 6

### 公开静态方法
> isLit(block: Block): boolean -> 检查方块是否处于点亮状态
> isContainer(block: Block): boolean -> 检查方块是否为容器（拥有物品栏）
> setLit(block: Block, lit: boolean): void -> 设置方块的点亮状态
> isCrop(material: XMaterial): boolean -> 检查材质是否为作物（已弃用，建议使用 XTag.CROPS）
> isDangerous(material: XMaterial): boolean -> 检查材质是否为危险方块（已弃用，建议使用 XTag.DANGEROUS_BLOCKS）
> getColor(block: Block): DyeColor -> 获取方块的颜色（如羊毛）
> isCake(material: Material): boolean -> 检查材质是否为蛋糕
> isWheat(material: Material): boolean -> 检查材质是否为小麦
> isSugarCane(material: Material): boolean -> 检查材质是否为甘蔗
> isBeetroot(material: Material): boolean -> 检查材质是否为甜菜根
> isNetherWart(material: Material): boolean -> 检查材质是否为地狱疣
> isCarrot(material: Material): boolean -> 检查材质是否为胡萝卜
> isMelon(material: Material): boolean -> 检查材质是否为西瓜
> isPotato(material: Material): boolean -> 检查材质是否为马铃薯
> getDirection(block: Block): BlockFace -> 获取方块的朝向
> setDirection(block: Block, facing: BlockFace): boolean -> 设置方块的朝向
> setType(block: Block, material: XMaterial, applyPhysics: boolean): boolean -> 设置方块的类型
> getAge(block: Block): int -> 获取方块的生长阶段
> setAge(block: Block, age: int): void -> 设置方块的生长阶段
> setColor(block: Block, color: DyeColor): boolean -> 设置方块的颜色
> setFluidLevel(block: Block, level: int): boolean -> 设置流体方块的液位
> getFluidLevel(block: Block): int -> 获取流体方块的液位
> isWaterStationary(block: Block): boolean -> 检查水方块是否为静止状态
> isWater(material: Material): boolean -> 检查材质是否为水
> isLava(material: Material): boolean -> 检查材质是否为岩浆
> isOneOf(block: Block, blocks: Collection<String>): boolean -> 检查方块是否为指定集合中的一种（已弃用，建议使用 XTag.anyMatch）
> setCakeSlices(block: Block, amount: int): void -> 设置蛋糕的剩余切片数
> addCakeSlices(block: Block, slices: int): int -> 增加蛋糕的切片数并返回剩余切片数
> setEnderPearlOnFrame(endPortalFrame: Block, eye: boolean): void -> 设置末地传送门框架是否有末影之眼
> isSimilar(block: Block, material: XMaterial): boolean -> 检查方块是否与指定材质相似
> isAir(material: Material): boolean -> 检查材质是否为空气
> isPowered(block: Block): boolean -> 检查方块是否被充能
> setPowered(block: Block, powered: boolean): void -> 设置方块的充能状态
> isOpen(block: Block): boolean -> 检查方块是否处于打开状态
> setOpened(block: Block, opened: boolean): void -> 设置方块的打开状态

### 类内可被访问字段
> ISFLAT: boolean -> 判断当前服务器版本是否为扁平化版本（1.13+）
> ITEM_TO_BLOCK: Map<XMaterial, XMaterial> -> 物品到方块的映射关系

### 类方法
> private XBlock(): void -> 私有构造方法，防止实例化

## 实现细节
- 使用 ISFLAT 标志区分新旧 API，支持 1.13 前后的 Minecraft 版本
- 对于旧版本，使用 MaterialData API 进行方块操作
- 对于新版本，使用 BlockData API 进行方块操作
- 通过 BlockMaterial 枚举缓存旧版本的材质，避免版本兼容性问题
- 提供 ITEM_TO_BLOCK 映射，处理物品到方块的转换关系

## 使用场景
> 跨版本插件开发，需要操作方块属性（如方向、颜色、生长阶段等）
> 需要检测特定类型方块（如作物、危险方块等）
> 需要修改方块状态（如点亮、开关门等）
> 处理流体方块的液位变化

## 注意事项
> 部分方法已被弃用，建议使用 XTag 相关功能代替
> 该类不支持也不应该支持被标记为 isLegacy() 的材质
> 在使用前应确保传入的方块类型与方法预期的类型匹配，否则可能会抛出异常
> 对于不同版本的 Minecraft，某些方法的行为可能略有不同

