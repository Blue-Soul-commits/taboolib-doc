# Action

## 基本信息
- 类名和包路径: taboolib.module.ui.type.Action
- 基本用途: 定义TabooLib菜单系统中的抽象动作基类，用于处理菜单交互的核心逻辑
- 类型: 抽象类（Abstract Class）
- 所属模块: bukkit-ui

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> getCursor(e: ClickEvent): ItemStack? -> 抽象方法，获取点击事件中光标上的物品
> setCursor(e: ClickEvent, item: ItemStack?) -> 抽象方法，设置点击事件中光标上的物品
> getCurrentSlot(e: ClickEvent): Int -> 抽象方法，获取点击事件中当前操作的槽位索引

## 实现细节
- Action是一个抽象基类，定义了处理菜单交互所需的基本方法
- 包含三个抽象方法，需要子类实现以提供具体的交互逻辑
- 设计为与ClickEvent紧密配合，所有方法都接收ClickEvent参数
- 作为TabooLib菜单系统中的核心组件，负责处理物品移动和槽位操作

## 使用场景
> 作为自定义菜单交互逻辑的基类
> 在TabooLib菜单系统中，处理不同类型的点击和拖拽操作
> 在需要精确控制物品移动和槽位交互的场景中使用

## 注意事项
> 此类是抽象类，不能直接实例化，必须通过子类实现抽象方法
> 与ClickEvent类紧密关联，使用时需要理解ClickEvent的结构和属性
> 实现子类时应确保三个抽象方法的正确实现，以保证菜单交互的正常工作
> 通常不需要直接继承此类，而是使用TabooLib提供的现有实现
