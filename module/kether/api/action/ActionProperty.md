# ActionProperty

## 基本信息
- 类名和包路径: taboolib.module.kether.action.ActionProperty
- 基本用途: Kether脚本引擎中用于处理对象属性访问的工具类和动作实现
- 类型: 单例对象(object)及内部类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> getScriptProperty(obj: Any): Collection<ScriptProperty<*>> -> 获取适用于给定对象的所有属性处理器
> getScriptProperty(obj: Any, key: String): Any? -> 获取给定对象指定键的属性值

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- ActionProperty是一个单例对象，包含两个内部类Set和Get，分别用于设置和获取对象属性
- getScriptProperty(obj)方法根据对象类型找到所有适用的ScriptProperty，并按照类继承关系远近排序
- 排序规则确保最贴近对象实际类型的属性处理器优先被使用
- getScriptProperty(obj, key)方法尝试使用每个适用的属性处理器读取指定键的值，直到成功
- Set类实现了属性设置动作，接收目标实例、属性键和要设置的值
- Get类实现了属性获取动作，接收目标实例和属性键
- 所有操作都支持异步执行，返回CompletableFuture

## 使用场景
> 在Kether脚本中访问和修改对象的属性
> 实现"对象.属性"语法形式
> 提供统一的属性访问机制，支持不同类型的对象
> 结合ScriptProperty系统，为不同类型对象提供自定义属性处理

## 注意事项
> 当对象为null或属性不支持时，会输出警告信息而不是抛出异常
> 属性访问基于已注册的ScriptProperty，如果没有找到合适的处理器，操作将失败
> 警告信息支持国际化，使用t()函数翻译
> 文件使用@Suppress("UNCHECKED_CAST")注解，抑制了不安全类型转换的警告
