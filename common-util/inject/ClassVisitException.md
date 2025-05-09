# ClassVisitException

## 基本信息
- 类名和包路径: taboolib.common.inject.ClassVisitException
- 基本用途: 在类访问过程中发生异常时提供详细的错误信息
- 类型: 异常类(Exception Class)
- 所属模块: TabooLib 注入模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> ClassVisitException(clazz: Class<?>, cause: Throwable): Constructor -> 创建一个包含类信息的异常
> ClassVisitException(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle, cause: Throwable): Constructor -> 创建一个包含类、访问组和生命周期信息的异常
> ClassVisitException(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle, field: ClassField, cause: Throwable): Constructor -> 创建一个包含类、访问组、生命周期和字段信息的异常
> ClassVisitException(clazz: ReflexClass, group: VisitorGroup, lifeCycle: LifeCycle, method: ClassMethod, cause: Throwable): Constructor -> 创建一个包含类、访问组、生命周期和方法信息的异常

## 实现细节
- 继承自 RuntimeException，是一个非受检异常
- 提供多个构造函数，支持不同级别的错误信息详细程度
- 在错误消息中包含类名、访问组、生命周期以及可能的字段或方法名
- 保留原始异常作为 cause

## 使用场景
> 在类访问器(ClassVisitor)处理过程中捕获和包装异常
> 在依赖注入或反射操作过程中提供更详细的错误信息
> 在生命周期事件处理中标识错误来源

## 注意事项
> 作为 RuntimeException 的子类，不需要显式捕获或声明
> 异常消息格式为 "类名[#成员名]: 访问组 (生命周期)"
> 应当在捕获此异常时记录完整的异常信息，以便调试