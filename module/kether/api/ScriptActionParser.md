# ScriptActionParser

## 基本信息
- 类名和包路径: taboolib.module.kether.ScriptActionParser
- 基本用途: Kether脚本引擎的动作解析器包装类，简化动作解析器的创建
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> reader: QuestReader.() -> QuestAction<*> -> 用于解析脚本动作的函数对象

### 类方法
> resolve<T>(resolver: QuestReader): QuestAction<T> -> 实现QuestActionParser接口的方法，调用reader函数解析动作

## 实现细节
- ScriptActionParser实现了QuestActionParser接口，提供了更简洁的动作解析器创建方式
- 使用函数类型作为构造参数，允许以lambda表达式形式定义解析逻辑
- reader函数是QuestReader的扩展函数，可以直接访问QuestReader的方法
- resolve方法内部使用了不安全的类型转换(as QuestAction<T>)，将任意类型的QuestAction转换为指定类型
- 使用@Suppress("UNCHECKED_CAST")注解抑制了不安全类型转换的警告

## 使用场景
> 创建Kether脚本动作的解析器
> 简化动作解析器的实现，使用更简洁的lambda语法
> 与@KetherParser注解配合，注册自定义动作到Kether脚本引擎
> 作为自定义动作类的伴生对象方法，提供动作解析功能

## 注意事项
> 类型参数T仅用于构造类型，实际使用时通过resolve方法的类型参数指定
> resolve方法中的类型转换可能导致运行时类型错误，需确保reader函数返回正确类型
> 通常与scriptParser扩展函数配合使用，进一步简化解析器创建
> 在动作解析过程中可能抛出异常，应当妥善处理
