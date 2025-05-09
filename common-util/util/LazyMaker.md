# LazyMaker

## 基本信息
- 类名和包路径: taboolib.common.util.LazyMaker
- 基本用途: 提供增强的延迟加载工具
- 类型: Kotlin工具类和扩展函数
- 所属模块: common-util

## 函数和类
### 全局函数
> unsafeLazy<T>(initializer: () -> T): Lazy<T> -> 创建线程不安全的延迟加载对象
> resettableLazy<T>(vararg groups: String, synchronized: Boolean = false, initializer: () -> T): ResettableLazy<T> -> 创建可重置的延迟加载对象

### 类
> ResettableLazy<T> -> 可重置的延迟加载抽象类
> ResettableLazyImpl<T> -> 非线程安全的可重置延迟加载实现
> ResettableSynchronizedLazyImpl<T> -> 线程安全的可重置延迟加载实现
> UninitializedValue -> 表示未初始化值的单例对象

## 实现细节
### unsafeLazy
- 使用Kotlin标准库的`lazy`函数，指定`LazyThreadSafetyMode.NONE`模式
- 提供更直观的API来创建非线程安全的延迟加载对象

### resettableLazy
- 根据`synchronized`参数选择线程安全或非线程安全实现
- 将创建的延迟加载对象注册到全局缓存中，以便后续重置

### ResettableLazy
- 继承自Kotlin标准库的`Lazy`接口
- 添加`reset()`方法支持重置值
- 使用Guava的`Cache`实现弱引用存储所有实例
- 提供按组重置功能

### 实现类
- 两个实现类分别处理线程安全和非线程安全情况
- 使用`UninitializedValue`对象标记未初始化状态
- 线程安全版本使用`@Volatile`和`synchronized`确保线程安全
- 两个实现都支持`toString()`方法显示初始化状态

## 使用场景
> 需要延迟初始化但可能需要重置的对象
> 按组管理和重置相关的延迟加载对象
> 需要非线程安全延迟加载以提高性能
> 需要在特定条件下重新计算延迟加载的值

## 注意事项
> 使用`unsafeLazy`在多线程环境可能导致竞态条件
> 重置延迟加载对象会导致下次访问时重新计算
> 使用弱引用存储实例，不会阻止垃圾回收
> 组名为空字符串的对象只能通过`reset("*")`或空参数`reset()`重置
