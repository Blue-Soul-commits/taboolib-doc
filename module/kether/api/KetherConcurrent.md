# KetherConcurrent

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherConcurrent
- 基本用途: 提供CompletableFuture的扩展函数，简化Kether脚本中的异步操作和类型转换
- 类型: 扩展函数集合
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> str<T>(then: (String) -> T): CompletableFuture<T> -> 将Future的结果转换为字符串，并应用转换函数
> strOrNull<T>(then: (String?) -> T): CompletableFuture<T> -> 将Future的结果转换为可空字符串，并应用转换函数
> bool<T>(then: (Boolean) -> T): CompletableFuture<T> -> 将Future的结果转换为布尔值，并应用转换函数
> int<T>(then: (Int) -> T): CompletableFuture<T> -> 将Future的结果转换为整数，并应用转换函数
> long<T>(then: (Long) -> T): CompletableFuture<T> -> 将Future的结果转换为长整数，并应用转换函数
> double<T>(then: (Double) -> T): CompletableFuture<T> -> 将Future的结果转换为双精度浮点数，并应用转换函数
> float<T>(then: (Float) -> T): CompletableFuture<T> -> 将Future的结果转换为单精度浮点数，并应用转换函数
> orNull<T>(): T? -> 获取Future的当前结果，如果未完成则返回null
> except<T>(): CompletableFuture<T> -> 处理Future的异常，打印堆栈并返回null
> except<T>(fn: (Throwable) -> T): CompletableFuture<T> -> 处理Future的异常，打印堆栈并应用转换函数
> exceptNull<T>(fn: (Throwable) -> Unit): CompletableFuture<T> -> 处理Future的异常，执行函数后返回null

### 类内可被访问字段
> 无

### 类方法
> 无（文件中只包含扩展函数）

## 实现细节
- 所有类型转换函数都扩展自CompletableFuture<Any?>类型，提供类型安全的转换
- 使用Coerce工具类进行类型强制转换，提供更灵活的类型处理
- 类型转换函数都包含异常处理，当转换失败时会提供默认值
- str和strOrNull函数会自动对字符串进行trimIndent处理，移除缩进
- except系列函数提供了不同的异常处理方式，方便根据需求处理异常情况
- 所有扩展函数保持了CompletableFuture的异步特性，允许链式调用

## 使用场景
> 在Kether脚本中简化异步操作的类型转换和异常处理
> 将脚本执行结果安全地转换为所需类型
> 处理异步操作中可能出现的异常
> 链式调用多个异步操作，提高代码可读性

## 注意事项
> 类型转换失败时会返回默认值（如空字符串、0、false等），而不是抛出异常
> except系列函数会打印异常堆栈，便于调试
> orNull函数会立即获取结果，如果Future未完成则返回null，不会等待完成
> 适用于Kether脚本中的异步执行流程，简化了异步编程模型
