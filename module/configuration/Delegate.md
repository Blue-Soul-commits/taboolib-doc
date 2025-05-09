# Delegate
## 基本信息
- 类名和包路径: taboolib.module.configuration.util.Delegate
- 基本用途: 提供配置属性的委托功能，简化配置值的读写操作
- 类型: 类 (Class) 和顶层函数
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> config(config: KProperty0<Configuration>, path: String? = null): Delegate -> 创建配置委托对象

### 类内可被访问字段
> config: KProperty0<Configuration> -> 配置对象的属性引用
> path: String? -> 配置路径，为 null 时使用属性名

### 类方法
> getValue<R, T>(thisRef: R, property: KProperty<*>): T -> 获取配置值，支持自动类型转换
> setValue<R, T : Any>(thisRef: R, property: KProperty<*>, value: T) -> 设置配置值，支持自动序列化

## 实现细节
- 使用 Kotlin 的属性委托机制，通过 by 关键字简化配置值的访问
- 支持通过属性名自动映射配置路径，也可以指定自定义路径
- 在读取值时，如果值是 ConfigurationSection 类型，会自动反序列化为对象
- 在写入值时，根据值的类型选择直接设置或序列化为配置节点
- 使用 inline 和 reified 关键字实现泛型类型的运行时访问
- 支持基本类型、集合、映射和自定义对象的读写

## 使用场景
> 简化配置值的读写操作，避免重复的配置路径字符串
> 将配置值与类属性直接绑定，提高代码可读性
> 支持自定义对象的自动序列化和反序列化
> 在多个组件中共享配置访问逻辑

## 注意事项
> 委托属性的类型必须与配置值的类型兼容，否则会抛出类型转换错误
> 自定义对象需要有默认构造函数，才能正确反序列化
> 配置对象必须通过属性引用 (KProperty0) 传入，通常使用 :: 操作符
> 当配置值不存在或类型不匹配时，会抛出错误而不是返回 null
