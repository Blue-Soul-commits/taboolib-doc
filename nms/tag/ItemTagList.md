# ItemTagList

## 基本信息
- 类名和包路径: taboolib.module.nms.ItemTagList
- 基本用途: 表示 NBT 列表类型数据，用于存储和操作 Minecraft 物品 NBT 中的列表数据
- 类型: 具体类，同时实现了 ItemTagData 和 MutableList<ItemTagData> 接口
- 所属模块: bukkit-nms-tag

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> of(vararg list: ItemTagData): ItemTagList -> 通过多个 ItemTagData 对象创建 ItemTagList
> of(vararg list: Any): ItemTagList -> 通过多个任意类型对象创建 ItemTagList，会自动将对象转换为对应的 ItemTagData

### 类内可被访问字段
> value: CopyOnWriteArrayList<ItemTagData> -> 存储列表中的 ItemTagData 元素

### 类方法
> constructor() -> 创建一个空的 ItemTagList
> constructor(list: List<ItemTagData>) -> 通过已有的 ItemTagData 列表创建 ItemTagList
> asList(): ItemTagList -> 返回自身作为 ItemTagList
> toJsonSimplified(): String -> 将列表转换为简化的 JSON 字符串
> toJsonSimplified(index: Int): String -> 将列表转换为带有指定缩进的简化 JSON 字符串
> toArray(): Array<ItemTagData> -> 将列表转换为 ItemTagData 数组
> toArray(p0: Array<out T>): Array<out T> -> 将列表转换为指定类型的数组

## 实现细节
- 使用 CopyOnWriteArrayList 作为内部存储结构，提供线程安全的列表操作
- 继承自 ItemTagData，表示这是一个 NBT 数据类型，类型为 LIST
- 实现 MutableList<ItemTagData> 接口，提供标准的列表操作方法
- 重写了 toString() 方法，调用 saveToString() 方法将列表转换为字符串表示

## 使用场景
> 在处理 Minecraft 物品 NBT 数据时，用于表示和操作列表类型的 NBT 数据
> 在创建或修改物品 NBT 时，用于构建列表类型的数据结构
> 在序列化和反序列化 NBT 数据时，用于处理列表类型的数据

## 注意事项
> ItemTagList 是线程安全的，因为它使用了 CopyOnWriteArrayList 作为内部存储
> 在添加元素时，确保元素是 ItemTagData 类型或可以转换为 ItemTagData 类型的对象
