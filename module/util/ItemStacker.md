# ItemStacker

## 基本信息
- 类名和包路径: taboolib.module.ui.ItemStacker
- 基本用途: 物品背包合并工具，用于处理物品在不同背包间的移动、合并和拆分
- 类型: 抽象类
- 所属模块: taboolib.module.ui

## 类结构

### 公开静态字段
> MINECRAFT: ItemStacker -> 默认的 Minecraft 物品堆叠实现，使用物品自身的最大堆叠数

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> getMaxStackSize(itemStack: ItemStack): int -> 获取物品的最大堆叠数量
> moveItemFromChest(item: ItemStack, player: Player): void -> 从箱子里移动物品到玩家背包，溢出则丢弃
> addItemAndSplit(item: ItemStack, inventory: Inventory, start: int): boolean -> 添加并拆分物品，不合并，返回是否添加完成
> addItemAndSplit(item: ItemStack, inventory: Inventory, start: int, desc: boolean): boolean -> 添加并拆分物品，可选是否从快捷栏逆向添加
> addItemFromChestToPlayer(item: ItemStack, inventory: Inventory): boolean -> 从箱子添加物品到玩家背包
> addItemAndMerge(item: ItemStack, inventory: Inventory, ignore: List<Integer>): AddResult -> 合并物品到已有堆叠，不新增物品槽位

## 实现细节
- 提供了一个默认实现 MINECRAFT，使用物品自身的最大堆叠数
- 抽象方法 getMaxStackSize 允许子类自定义物品的最大堆叠数量
- 内部使用 check 方法处理物品放入背包槽位的逻辑
- 包含内部类 AddResult 用于返回物品合并操作的结果
- 针对 PlayerInventory 和 CraftingInventory 有特殊处理，限制大小为 36 格
- 支持从快捷栏逆向添加物品，模拟工作台操作

## 使用场景
> 从容器向玩家背包移动物品时，自动处理物品堆叠和溢出
> 自定义界面中处理物品的移动和合并
> 实现自定义的物品堆叠规则，如允许某些物品超过原版堆叠上限

## 注意事项
> 修改物品数量时会直接修改传入的 ItemStack 对象，需注意引用问题
> 添加物品到背包时，会优先尝试合并到已有物品堆叠，再尝试放入空槽位
> 对于玩家背包，会区分快捷栏(0-8)和主背包(9-35)区域
> 当物品无法完全放入背包时，moveItemFromChest 方法会将剩余物品丢弃到玩家所在位置
