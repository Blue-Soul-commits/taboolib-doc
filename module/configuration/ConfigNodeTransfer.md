# ConfigNodeTransfer
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConfigNodeTransfer
- 基本用途: 提供配置节点值的类型转换功能，支持懒加载和属性代理
- 类型: 类 (Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> conversion<T, R>(lazy: Boolean = false, block: T.() -> R): ConfigNodeTransfer<T, R> -> 创建配置值转换器
> lazyConversion<T, R>(block: T.() -> R): ConfigNodeTransfer<T, R> -> 创建懒加载模式的配置值转换器

### 类内可被访问字段
> isLazyMode: Boolean -> 是否为懒加载模式，只读属性
> configValue: Any? -> 原始配置值，内部属性
> cachedValue: Any? -> 转换后的缓存值，内部属性
> transfer: T.() -> R -> 转换函数，内部属性

### 类方法
> get(): R -> 获取转换后的值
> reset(configValue: Any) -> 重置配置值并刷新缓存
> getValue(thisRef: Any?, property: KProperty<*>): R -> 属性代理操作符，支持通过代理访问转换后的值

## 实现细节
- 使用泛型参数 T 和 R 分别表示原始类型和目标类型
- 支持懒加载模式，只在首次访问时执行转换操作
- 实现了 Kotlin 属性代理接口，可以通过 by 关键字使用
- 提供了两个辅助函数 conversion 和 lazyConversion 简化创建过程
- 使用 @Suppress("UNCHECKED_CAST") 注解抑制类型转换警告
- 在 ConfigNodeLoader 中被特殊处理，用于配置节点值的类型转换

## 使用场景
> 将配置文件中的复杂数据结构转换为自定义类型
> 需要延迟处理配置值的场景（懒加载模式）
> 通过属性代理简化配置值的访问和转换
> 在 @ConfigNode 注解的字段中使用，实现自动类型转换

## 注意事项
> 如果未设置配置值就调用 get() 方法，将抛出 "No value" 错误
> 懒加载模式下，转换操作只在首次访问时执行，适合耗时的转换操作
> 非懒加载模式下，转换操作在 reset() 时立即执行
> 使用属性代理时，底层调用的是 get() 方法

