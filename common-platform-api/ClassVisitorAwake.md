# ClassVisitorAwake
## 基本信息 
- 类名和包路径: taboolib.common.platform.ClassVisitorAwake
- 基本用途: 处理带有 @Awake 注解的方法，在指定的生命周期阶段调用这些方法
- 类型: Kotlin 类，继承自 ClassVisitor
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> lifeCycle: LifeCycle -> 当前访问器处理的生命周期阶段

### 类方法
> visit(method: ClassMethod, owner: ReflexClass): Unit -> 访问并处理带有 @Awake 注解的方法
> getLifeCycle(): LifeCycle -> 获取当前访问器处理的生命周期阶段

## 实现细节
- 继承自 ClassVisitor 类，用于扫描和处理类中的特定方法
- 构造函数接收一个 LifeCycle 参数，表示当前处理的生命周期阶段
- visit 方法检查方法上的 @Awake 注解，并获取其 value 属性值
- 如果 @Awake 注解的 value 值与当前生命周期阶段匹配，则调用该方法
- 对于实例方法，先获取类的实例再调用；对于静态方法，直接调用
- 如果 @Awake 注解缺少 value 参数，会输出警告信息

## 使用场景 
> 在 TabooLib 的生命周期管理系统中，自动调用标记了特定生命周期阶段的方法
> 实现插件在不同生命周期阶段的初始化和资源管理
> 提供一种声明式的方式来定义方法在何时被调用

## 注意事项 
> @Awake 注解必须指定 value 参数，否则会输出警告且方法不会被调用
> 被 @Awake 注解标记的方法应该与指定的生命周期阶段相关
> 静态方法和实例方法都可以使用 @Awake 注解，但处理方式不同
> 该类通常由 TabooLib 内部使用，不需要直接实例化
