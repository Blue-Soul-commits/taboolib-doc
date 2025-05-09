# VirtualStorageInventory

## 基本信息
- 类名和包路径: taboolib.module.ui.virtual.VirtualStorageInventory
- 基本用途: 虚拟玩家背包，用于在虚拟背包系统中模拟玩家的物品栏
- 类型: 类
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> sourceInventory: VirtualInventory -> 源虚拟背包实例
> delegateInventory: Inventory -> 委托背包实例，用于实际存储物品

### 类方法
> iterator(): MutableListIterator<ItemStack> -> 获取物品迭代器
> iterator(p0: Int): MutableListIterator<ItemStack> -> 从指定位置获取物品迭代器
> getSize(): Int -> 获取背包大小，固定为36
> getMaxStackSize(): Int -> 获取最大堆叠数量
> setMaxStackSize(p0: Int) -> 设置最大堆叠数量
> getItem(p0: Int): ItemStack -> 获取指定位置的物品
> setItem(p0: Int, p1: ItemStack?) -> 设置指定位置的物品
> addItem(vararg p0: ItemStack?): HashMap<Int, ItemStack> -> 添加物品
> removeItem(vararg p0: ItemStack?): HashMap<Int, ItemStack> -> 移除物品
> getContents(): Array<ItemStack> -> 获取所有物品
> setContents(p0: Array<out ItemStack>) -> 设置所有物品
> getStorageContents(): Array<ItemStack> -> 获取存储物品
> setStorageContents(p0: Array<out ItemStack>) -> 设置存储物品
> contains(p0: Material): Boolean -> 检查是否包含指定材质
> contains(p0: ItemStack?): Boolean -> 检查是否包含指定物品
> contains(p0: Material, p1: Int): Boolean -> 检查是否包含指定数量的材质
> contains(p0: ItemStack?, p1: Int): Boolean -> 检查是否包含指定数量的物品
> containsAtLeast(p0: ItemStack?, p1: Int): Boolean -> 检查是否至少包含指定数量的物品
> all(p0: Material): HashMap<Int, out ItemStack> -> 获取所有指定材质的物品
> all(p0: ItemStack?): HashMap<Int, out ItemStack> -> 获取所有指定物品
> first(p0: Material): Int -> 获取第一个指定材质的物品位置
> first(p0: ItemStack): Int -> 获取第一个指定物品的位置
> firstEmpty(): Int -> 获取第一个空位置
> isEmpty(): Boolean -> 检查背包是否为空
> remove(p0: Material) -> 移除所有指定材质的物品
> remove(p0: ItemStack) -> 移除所有指定物品
> clear(p0: Int) -> 清空指定位置
> clear() -> 清空背包
> getViewers(): MutableList<HumanEntity> -> 获取查看者列表，始终返回空列表
> getType(): InventoryType -> 获取背包类型，固定为CHEST
> getHolder(): InventoryHolder? -> 获取背包持有者，始终返回null
> getLocation(): Location? -> 获取背包位置，始终返回null

## 实现细节
- 实现Bukkit的Inventory接口，使其能够作为标准背包使用
- 使用委托模式，将大部分操作委托给delegateInventory实现
- 对于getItem和setItem等关键方法，通过sourceInventory进行操作，确保数据同步
- 初始化时从sourceInventory获取玩家背包内容

## 使用场景
> 在VirtualInventoryView中作为玩家背包部分
> 在RemoteInventory.createInventoryView方法中被创建
> 作为虚拟背包系统中玩家背包的代理

## 注意事项
> 此类固定大小为36，对应玩家背包的大小
> getViewers()始终返回空列表，因为虚拟背包系统自行管理查看者
> getType()固定返回CHEST类型，无论实际背包类型如何
