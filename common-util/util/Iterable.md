# Iteration

## 基本信息
- 类名和包路径: taboolib.common.util.Iteration
- 基本用途: 提供迭代和遍历工具函数
- 类型: Kotlin扩展函数文件
- 所属模块: common-util

## 扩展函数
> Iterable<T>.each(start: Int = -1, end: Int = -1, reversed: Boolean = false, action: Closeable.(index: Int, T) -> R?): R? -> 可中断的集合遍历
> Array<out K>.getFirst(get: (K) -> V?): V? -> 获取数组中第一个非空映射结果

## 实现细节
### each函数
- 创建一个实现`Closeable`接口的匿名对象作为触发器
- 支持正向和反向遍历
- 支持指定起始和结束索引
- 支持提前终止遍历(通过调用`close()`)
- 支持返回非空值来提前结束并返回结果

### getFirst函数
- 内联函数，减少Lambda表达式开销
- 遍历数组元素，对每个元素应用转换函数
- 返回第一个非空转换结果
- 如果所有转换结果都为空，则返回null

## 使用场景
> 需要在遍历过程中提前退出循环
> 需要从遍历中返回特定值
> 需要在特定范围内遍历集合
> 需要查找数组中第一个满足条件的元素

## 注意事项
> `each`函数在反向遍历时会先将集合转换为列表，可能会有性能影响
> 内联函数会在调用处展开，可能增加编译后代码体积
> 使用`close()`方法终止遍历时，后续元素不会被处理
