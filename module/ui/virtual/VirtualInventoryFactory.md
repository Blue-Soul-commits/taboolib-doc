# VirtualInventoryFactory

## 基本信息
- 文件名和包路径: taboolib.module.ui.virtual.VirtualInventoryFactory.kt
- 基本用途: 提供虚拟背包系统的工厂方法和扩展函数
- 类型: Kotlin文件（包含扩展函数）
- 所属模块: bukkit-ui

## 函数结构

### 公开扩展函数
> Inventory.virtualize(storageContents: List<ItemStack>? = null): VirtualInventory -> 将背包转换为虚拟背包实例
> HumanEntity.openVirtualInventory(inventory: VirtualInventory, updateId: Boolean = true): RemoteInventory -> 使玩家打开虚拟页面
> RemoteInventory.inject(menu: Basic): Unit -> 注入事件到Basic页面（转发到ChestImpl版本）
> RemoteInventory.inject(menu: Chest): Unit -> 注入事件到Chest页面（转发到ChestImpl版本）
> RemoteInventory.inject(menu: T: ChestImpl): Unit -> 注入事件到ChestImpl页面
> RemoteInventory.createInventoryView(): InventoryView -> 生成InventoryView实例

### 内部扩展函数
> internal Player.getStorageItems(): Array<ItemStack?> -> 获取重新排列后的背包物品（将0..8放到最后）

## 实现细节
- Inventory.virtualize: 创建VirtualInventory实例，可选择指定玩家背包内容
- HumanEntity.openVirtualInventory: 
  - 通过InventoryHandler打开虚拟背包
  - 设置remoteInventory引用
  - 将remoteInventory添加到playerRemoteInventoryMap
  - 触发InventoryOpenEvent事件
- RemoteInventory.inject: 
  - 注册点击回调，创建VirtualInventoryInteractEvent并传递给菜单
  - 注册关闭回调，处理菜单关闭逻辑
- RemoteInventory.createInventoryView: 
  - 根据Minecraft版本创建不同的InventoryView实现
  - 1.21+版本使用VirtualInventoryViewModern
  - 其他版本尝试使用VirtualInventoryView，失败则使用VirtualInventoryViewLegacy
- Player.getStorageItems: 重新排列玩家背包物品，将快捷栏(0..8)放到最后

## 使用场景
> 创建和打开虚拟背包
> 将普通背包转换为虚拟背包
> 将菜单系统与虚拟背包系统集成
> 处理虚拟背包的事件回调

## 注意事项
> 虚拟背包系统支持多个Minecraft版本，使用不同的实现
> 打开虚拟背包时会触发标准的Bukkit事件
> 注入事件到菜单时会处理异常，防止错误传播

