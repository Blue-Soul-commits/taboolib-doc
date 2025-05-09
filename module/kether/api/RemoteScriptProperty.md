# RemoteScriptProperty

## 基本信息
- 类名和包路径: taboolib.module.kether.RemoteScriptProperty
- 基本用途: Kether脚本引擎的远程属性处理器，实现跨插件/容器访问和操作对象属性
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remote: OpenContainer -> 远程容器实例，用于进行跨容器通信
> source: Any -> 远程ScriptProperty对象的原始引用

### 类方法
> read(instance: Any, key: String): OpenResult -> 从指定实例读取指定键的属性值
> write(instance: Any, key: String, value: Any?): OpenResult -> 向指定实例写入指定键的属性值

## 实现细节
- RemoteScriptProperty继承自ScriptProperty<Any>抽象类，使用Any作为泛型参数以支持任意类型
- 构造函数接收远程容器、远程属性处理器和ID参数
- read和write方法通过反射调用远程源对象的对应方法
- 使用OpenResult.cast静态方法将远程返回的结果转换为本地OpenResult对象
- 所有反射调用都使用remap=false，避免字段名映射问题

## 使用场景
> 跨插件访问和操作对象属性
> 在不同ClassLoader环境下共享属性处理功能
> 实现模块化的属性系统，一个插件可以使用另一个插件定义的属性处理器
> 与StandardChannel配合，支持远程注册和使用属性处理器

## 注意事项
> 使用反射调用，可能存在性能开销
> 依赖远程容器的可用性，如果远程容器不可用则操作失败
> 使用OpenResult.cast进行结果转换，确保跨容器正确传递结果
> 泛型类型固定为Any，可能导致类型安全性降低
> 通常不需要直接创建，而是通过StandardChannel.REMOTE_ADD_PROPERTY进行注册
