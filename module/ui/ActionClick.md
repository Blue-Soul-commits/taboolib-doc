# ActionClick

## 基本信息
- 类名和包路径: taboolib.module.ui.type.ActionClick
- 基本用途: 实现TabooLib菜单系统中的点击动作处理，用于处理普通点击交互
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
> getCursor(e: ClickEvent): ItemStack -> 获取点击事件中光标上的物品
> setCursor(e: ClickEvent, item: ItemStack?) -> 设置点击事件中光标上的物品
> getCurrentSlot(e: ClickEvent): Int -> 获取点击事件中当前操作的槽位索引

## 实现细节
- ActionClick继承自Action抽象类，实现了所有抽象方法
- getCursor方法直接返回点击事件中玩家光标上的物品
- setCursor方法直接设置点击事件中玩家光标上的物品
- getCurrentSlot方法直接返回点击事件中的原始槽位索引（rawSlot）
- 所有方法实现都非常简单直接，主要是委托给ClickEvent中的相关属性和方法

## 使用场景
> 在TabooLib菜单系统中，处理普通的点击交互
> 在自定义菜单实现中，作为默认的点击处理器
> 在需要标准点击行为的菜单组件中使用

## 注意事项
> 此类是Action抽象类的具体实现，专门用于处理普通点击交互
> getCursor方法返回值类型为非空的ItemStack，而不是ItemStack?，可能需要注意空值处理
> 与ClickEvent类紧密关联，使用时需要确保ClickEvent包含正确的clicker和rawSlot信息
> 通常不需要直接实例化此类，而是由TabooLib菜单系统内部使用
