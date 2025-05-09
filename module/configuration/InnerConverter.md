# InnerConverter
## 基本信息
- 类名和包路径: taboolib.module.configuration.InnerConverter
- 基本用途: 提供配置值与字段值之间的双向转换功能
- 类型: 类 (Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> toField: ClassMethod -> 用于将配置值转换为字段值的静态方法
> fromField: ClassMethod -> 用于将字段值转换为配置值的静态方法

### 类方法
> getConverter(field: Field, root: Any): Converter<Any, Any> -> 获取用于特定字段的转换器

## 实现细节
- 使用 NightConfig 库的 Converter 接口实现配置值与字段值之间的双向转换
- 通过 ClassMethod 对象调用静态方法实现转换逻辑
- 转换方法接收字段对象、值和根对象作为参数
- 在 toField 方法中，root 参数表示 ConfigurationSection 对象
- 在 fromField 方法中，root 参数表示包含该字段的对象

## 使用场景
> 在配置系统中实现自定义类型的序列化和反序列化
> 在对象与配置之间的转换过程中处理复杂类型
> 为 NightConfig 的 ObjectConverter 提供自定义类型的转换支持
> 在配置文件与对象映射过程中处理特殊字段

## 注意事项
> toField 和 fromField 方法必须是静态方法
> 转换方法必须返回非 null 值，否则会抛出空指针异常
> 转换方法的参数顺序固定为：字段对象、值、根对象
> 此类通常与 NightConfig 的对象转换系统配合使用
