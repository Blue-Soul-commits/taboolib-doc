# ActionKeyboard

## 基本信息
- 类名和包路径: taboolib.module.ui.type.ActionKeyboard
- 基本用途: 实现TabooLib菜单系统中的键盘快捷键动作处理，用于处理数字键交互
- 类型: 类（Class）
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> getCursor(e: ClickEvent): ItemStack? -> 获取点击事件中对应快捷栏槽位的物品
> setCursor(e: ClickEvent, item: ItemStack?) -> 设置点击事件中对应快捷栏槽位的物品
> getCurrentSlot(e: ClickEvent): Int -> 获取点击事件中当前操作的槽位索引

## 实现细节
- ActionKeyboard继承自Action抽象类，实现了所有抽象方法
- getCursor方法返回玩家背包中对应快捷键槽位（hotbarButton）的物品
- setCursor方法设置玩家背包中对应快捷键槽位（hotbarButton）的物品
- getCurrentSlot方法直接返回点击事件中的原始槽位索引（rawSlot）
- 与普通的ActionClick不同，此类操作的是玩家快捷栏中的物品，而非光标上的物品

## 使用场景
> 在TabooLib菜单系统中，处理玩家使用数字键（1-9）进行的快捷交互
> 在自定义菜单实现中，支持玩家通过数字键快速操作物品
> 在需要支持键盘快捷操作的高级菜单中使用

## 注意事项
> 此类是Action抽象类的具体实现，专门用于处理键盘数字键交互
> 使用此类时，需要确保ClickEvent中包含正确的clickEvent()方法，该方法应返回原始的Bukkit InventoryClickEvent
> hotbarButton属性对应玩家按下的数字键（0-8，对应键盘上的1-9）
> 与ActionClick不同，此类操作的是玩家快捷栏中的物品，而非光标上的物品