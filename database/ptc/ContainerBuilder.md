# ContainerBuilder

## 基本信息
- 类名和包路径: taboolib.expansion.ContainerBuilder
- 基本用途: 用于构建数据库容器的结构，定义数据列及其属性
- 类型: 开放类
- 所属模块: database-ptc

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> name: String -> 容器名称
> dataList: ArrayList<Data> -> 数据列列表

### 类方法
> data(name: String, length: Int = 64, int: Boolean = false, long: Boolean = false, double: Boolean = false, key: Boolean = false): Unit -> 添加数据列到容器中

## 实现细节
- 提供了一个内部类Data用于存储数据列的属性信息
- 提供了一个子类Flatten用于创建扁平化容器（键值对结构）
- 扁平化容器要求只有两个字段：一个键和一个值
- 支持不同数据类型的列定义，包括字符串、整数、长整数和双精度浮点数
- 支持将列标记为键，用于建立索引

## 使用场景
> 创建标准数据库容器，用于存储复杂结构的数据
> 创建扁平化容器，用于简单的键值对存储
> 定义数据库表结构，指定列名、长度和数据类型

## 注意事项
> 扁平化容器(Flatten)必须且只能有两个字段：一个键和一个值
> 如果未指定扁平化容器的字段，fixed()方法会自动添加默认的key和value字段
> 如果扁平化容器的字段数量不等于2，fixed()方法会抛出错误
> 数据类型(int, long, double)是互斥的，一个字段只能是其中一种类型

