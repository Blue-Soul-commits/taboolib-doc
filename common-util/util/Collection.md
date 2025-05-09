# Collection

## 基本信息
- 类名和包路径: taboolib.common.util.Collection
- 基本用途: 提供集合类的扩展函数
- 类型: Kotlin扩展函数文件
- 所属模块: common-util

## 扩展函数
### Any类扩展
> Any.asList(): List<String> -> 将任意对象转换为字符串列表

### MutableList扩展
> MutableList<T>.setSafely(index: Int, element: T, def: T): Unit -> 安全设置列表指定位置的元素
> MutableList<T>.addSafely(index: Int, element: T, def: T): Unit -> 安全在列表指定位置添加元素

### MutableCollection扩展
> MutableCollection<T>.removeAndBackIf(con: (T) -> Boolean): List<T> -> 根据条件删除元素并返回被删除的元素

### 全局函数
> join(args: List<String>, start: Int = 0, separator: String = " "): String -> 连接列表元素为字符串(已弃用)
> join(args: Array<String>, start: Int = 0, separator: String = " "): String -> 连接数组元素为字符串(已弃用)
> subList<T>(list: List<T>, start: Int = 0, end: Int = list.size): List<T> -> 获取子列表(已弃用)
> subMap<K, V>(map: Map<K, V>, start: Int = 0, end: Int = map.size - 1): List<Map.Entry<K, V>> -> 获取部分Map条目(已弃用)

## 实现细节
- `asList()`根据对象类型智能转换为字符串列表
- `setSafely()`和`addSafely()`自动填充列表空缺位置
- `removeAndBackIf()`使用惰性初始化避免创建不必要的列表
- 已弃用的函数提供了向后兼容性，建议使用Kotlin标准库函数

## 使用场景
> 需要将各种类型对象转换为字符串列表
> 需要安全地操作列表特定位置
> 需要在删除元素的同时获取被删除的元素
> 需要兼容旧代码

## 注意事项
> 已弃用的函数在未来版本可能会被移除
> `setSafely()`和`addSafely()`在索引远大于当前大小时可能会创建大量默认元素
> `removeAndBackIf()`是内联函数，可能会增加代码体积