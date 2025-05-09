# StorableChestImpl

## 基本信息
- 类名和包路径: taboolib.module.ui.type.impl.StorableChestImpl
- 基本用途: 实现可存储物品的容器界面
- 类型: 开放类
- 所属模块: taboolib.module.ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> rule: RuleImpl -> 页面规则实现

### 类方法
> rule(rule: StorableChest.Rule.() -> Unit): Unit -> 定义页面规则
> onClick(bind: Int, callback: (event: ClickEvent) -> Unit): Unit -> 点击事件回调，仅在特定位置下触发
> onClick(bind: Char, callback: (event: ClickEvent) -> Unit): Unit -> 点击事件回调，仅在特定位置下触发
> onClick(lock: Boolean, callback: (event: ClickEvent) -> Unit): Unit -> 点击事件回调，可选是否自动锁定点击位置
> build(): Inventory -> 构建页面

## 实现细节
- 继承自ChestImpl，实现了StorableChest接口
- 通过RuleImpl内部类实现StorableChest.Rule接口，提供物品存取规则
- 重写了onClick方法，相比于Basic类，处理了DRAG类型的点击事件
- 在build方法中实现了物品存取逻辑，包括：
  - 处理拖拽事件，阻止页面内的拖拽行为
  - 处理点击事件，阻止无法处理的合并行为
  - 实现自动装填功能，当玩家Shift+点击背包物品时，自动放入有效位置
  - 根据不同的点击类型选择不同的Action处理类
  - 根据规则检查物品是否可以放入指定位置
- RuleImpl类提供了多种规则设置方法，包括：
  - checkSlot: 检查物品是否可以放入指定位置
  - firstSlot: 获取页面中首个有效的位置
  - writeItem: 物品写入回调
  - readItem: 读取物品回调

## 使用场景
> 需要玩家能够存取物品的界面，如背包、仓库等
> 需要自定义物品存取规则的界面
> 需要处理特殊点击行为的界面

## 注意事项
> 虚拟化页面时无法更改规则
> 自动装填功能只会在目标位置为空时生效，不会覆盖已有物品
> 使用前需要通过rule方法设置规则，否则使用默认规则
> 默认规则允许所有物品放入任何位置，但不提供自动装填功能

