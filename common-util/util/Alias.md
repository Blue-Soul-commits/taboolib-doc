# Alias

## 基本信息
- 类名和包路径: taboolib.common.util.Alias
- 基本用途: 提供常用类型的别名定义
- 类型: Kotlin类型别名文件
- 所属模块: common-util

## 类型别名
> MatrixList<T> = List<List<T>> -> 表示二维列表或矩阵
> MapList<K, V> = List<Map<K, V>> -> 表示映射列表
> ProxyVector = Vector -> Vector类的代理类型
> ProxyLocation = Location -> Location类的代理类型

## 实现细节
- 使用Kotlin的`typealias`关键字定义类型别名
- 不包含实际实现代码，仅提供类型引用
- `ProxyVector`和`ProxyLocation`用于跨平台兼容性

## 使用场景
> 简化复杂类型的声明
> 提高代码可读性
> 统一跨平台API
> 在不同实现间提供兼容层

## 注意事项
> 类型别名不会创建新类型，只是现有类型的引用
> IDE通常会显示原始类型而非别名
> 类型别名可以提高代码可读性，但过度使用可能导致混淆
