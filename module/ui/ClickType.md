# ClickType

## 基本信息
- 类名和包路径: taboolib.module.ui.ClickType
- 基本用途: 定义TabooLib菜单系统中的点击类型枚举，用于区分不同的交互方式
- 类型: 枚举（Enum）
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> CLICK -> 表示普通的点击交互
> DRAG -> 表示拖拽物品的交互
> VIRTUAL -> 表示虚拟背包系统中的点击交互

### 公开静态方法
> values(): Array<ClickType> -> 返回包含所有枚举常量的数组（Enum默认方法）
> valueOf(name: String): ClickType -> 返回指定名称的枚举常量（Enum默认方法）

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 无额外类方法

## 实现细节
- ClickType是一个简单的枚举类，定义了三种基本的点击交互类型
- CLICK表示玩家通过鼠标点击背包槽位的普通交互
- DRAG表示玩家通过拖拽方式在背包中移动物品的交互
- VIRTUAL表示在TabooLib虚拟背包系统中发生的点击交互，通常由内部系统触发

## 使用场景
> 在菜单点击事件处理中，区分不同类型的交互方式
> 在虚拟背包系统中，标识特殊的点击类型
> 在自定义菜单实现中，根据点击类型执行不同的逻辑

## 注意事项
> 此枚举类型非常简单，仅包含三个常量值
> 与Bukkit原生的InventoryClickEvent.ClickType不同，此枚举更加简化，专注于TabooLib菜单系统的需求
> VIRTUAL类型主要用于TabooLib内部的虚拟背包系统，普通开发者较少直接使用
> 在处理菜单点击事件时，应根据不同的点击类型实现相应的逻辑
