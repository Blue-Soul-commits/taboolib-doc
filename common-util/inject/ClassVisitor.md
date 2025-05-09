# ClassVisitor

## 基本信息
- 类名和包路径: taboolib.common.inject.ClassVisitor
- 基本用途: 提供类、字段和方法的访问机制，用于依赖注入和反射操作
- 类型: 抽象类(Abstract Class)
- 所属模块: TabooLib 注入模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> findInstance(rClass: ReflexClass): Object? -> 查找 ReflexClass 的实例

### 类内可被访问字段
> priority: byte -> 访问器的优先级

### 类方法
> ClassVisitor(): Constructor -> 创建优先级为0的访问器
> ClassVisitor(priority: byte): Constructor -> 创建指定优先级的访问器
> getLifeCycle(): LifeCycle -> 获取访问器的生命周期
> visitStart(clazz: ReflexClass): void -> 当类开始加载时调用
> visitEnd(clazz: ReflexClass): void -> 当类结束加载时调用
> visit(field: ClassField, owner: ReflexClass): void -> 当字段加载时调用
> visit(method: ClassMethod, owner: ReflexClass): void -> 当方法加载时调用
> getPriority(): byte -> 获取访问器的优先级

## 实现细节
- 抽象类设计，要求子类实现 getLifeCycle() 方法
- 提供默认的空实现方法，子类可以选择性地覆盖需要的方法
- 支持优先级机制，通过构造函数设置
- 静态方法 findInstance 提供查找类实例的功能，先从 TabooLib.getAwakenedClasses() 中查找，再从 Kotlin 伴生类和单例类中查找

## 使用场景
> 实现依赖注入系统
> 在类加载过程中执行自定义操作
> 访问和处理类的字段和方法
> 在特定生命周期阶段执行代码

## 注意事项
> 必须实现 getLifeCycle() 方法以指定访问器在哪个生命周期阶段执行
> 优先级值越高，访问器执行顺序越靠前
> 默认优先级为0
> 访问方法提供了默认的空实现，只需覆盖需要的方法
