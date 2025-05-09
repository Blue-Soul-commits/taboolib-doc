# ObjectConverter
## 基本信息
- 类名和包路径: com.electronwill.nightconfig.core.conversion.ObjectConverter
- 基本用途: 将Java对象转换为配置文件格式，或将配置文件转换为Java对象
- 类型: 工具类
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> bypassTransient: boolean -> 是否处理标记为transient的字段
> bypassFinal: boolean -> 是否处理标记为final的字段
> ignoreConstructor: boolean -> 是否忽略构造函数，使用unsafe方式创建实例

### 类方法
> ObjectConverter() -> 创建默认转换器，等同于ObjectConverter(false, true)
> ObjectConverter(bypassTransient: boolean, bypassFinal: boolean) -> 创建具有高级参数的转换器
> ObjectConverter(ignoreConstructor: boolean) -> 创建可忽略构造函数的转换器
> setIgnoreConstructor(ignoreConstructor: boolean): ObjectConverter -> 设置是否忽略构造函数
> toConfig(o: Object, destination: Config): void -> 将对象转换为配置
> toConfig(clazz: Class<?>, destination: Config): void -> 将类的静态字段转换为配置
> toConfig(o: Object, destinationSupplier: Supplier<C>): C -> 将对象转换为配置，并返回配置
> toConfig(clazz: Class<?>, destinationSupplier: Supplier<C>): C -> 将类的静态字段转换为配置，并返回配置
> toObject(config: UnmodifiableConfig, destination: Object): void -> 将配置转换为对象
> toObject(config: UnmodifiableConfig, destinationSupplier: Supplier<O>): O -> 将配置转换为对象，并返回对象

## 实现细节
- 支持通过注解自定义字段路径
- 支持自定义转换器，通过@Converter注解或内置转换器
- 支持嵌套对象和集合的转换
- 支持枚举类型的转换
- 支持通过反射创建对象实例，可选择绕过构造函数
- 支持处理类的继承层次结构
- 支持处理泛型集合和嵌套集合
- 使用AnnotationUtils处理字段和类的注解

## 使用场景
> 将Java对象序列化到配置文件中，如YAML、HOCON等格式
> 从配置文件反序列化数据到Java对象
> 在TabooLib中用于配置文件与对象模型之间的转换
> 支持复杂对象结构的序列化和反序列化

## 注意事项
> 默认情况下不处理transient字段，但会处理final字段
> 可以通过设置ignoreConstructor=true来绕过构造函数创建对象
> 转换过程中会自动处理集合类型和嵌套对象
> 支持UUID和Map类型的自动转换
> 支持通过内置转换器实现自定义类型转换
