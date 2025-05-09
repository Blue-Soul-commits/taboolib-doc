# ScriptProperty

## 基本信息
- 类名和包路径: taboolib.module.kether.ScriptProperty
- 基本用途: Kether脚本引擎中的属性访问抽象类，为对象属性的读写提供统一接口
- 类型: 抽象类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> id: String -> 属性标识符，用于在属性注册表中唯一标识该属性

### 类方法
> read(instance: T, key: String): OpenResult -> 抽象方法，从指定实例读取指定键的属性值
> write(instance: T, key: String, value: Any?): OpenResult -> 抽象方法，向指定实例写入指定键的属性值

## 实现细节
- ScriptProperty是一个泛型抽象类，T表示可以处理的对象类型
- 构造函数接收一个id参数，用于标识该属性处理器
- 提供了两个抽象方法read和write，子类必须实现这些方法以提供属性读写功能
- 读写操作都返回OpenResult对象，表示操作的成功或失败状态
- 与KetherProperty注解配合使用，为不同类型的对象提供属性访问机制

## 使用场景
> 在Kether脚本中实现对象属性的访问
> 为自定义类型提供属性读写支持
> 与ActionProperty配合，实现"对象.属性"语法
> 构建对象属性的访问层，提供统一的接口

## 注意事项
> 子类必须实现read和write方法，定义属性读写的具体逻辑
> 返回的OpenResult应正确反映操作结果，包括成功状态和返回值
> 属性id应当唯一，避免在同一类型中发生冲突
> 通常与Kether.registeredScriptProperty集合配合使用，注册和管理属性处理器
