# ClassVisitorSchedule
## 基本信息 
- 类名和包路径: taboolib.common.platform.ClassVisitorSchedule
- 基本用途: 处理带有 @Schedule 注解的方法，将其注册为定时任务
- 类型: Kotlin 类，继承自 ClassVisitor
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> 无类内可被访问字段

### 类方法
> visit(method: ClassMethod, owner: ReflexClass): Unit -> 访问并处理带有 @Schedule 注解的方法
> getLifeCycle(): LifeCycle -> 获取当前访问器处理的生命周期阶段

## 实现细节
- 继承自 ClassVisitor 类，用于扫描和处理类中的特定方法
- 使用 @Awake 和 @Inject 注解标记，表示在 TabooLib 启动时自动注册
- 优先级设置为 1，确保在适当的时机处理
- visit 方法检查方法上的 @Schedule 注解，并获取其属性值
- 使用 submit 函数创建定时任务，根据注解中的 async、delay 和 period 参数配置任务
- 对于实例方法，先获取类的实例再调用；对于静态方法，直接调用
- 在 LifeCycle.ACTIVE 生命周期阶段执行，确保插件完全加载后才注册定时任务

## 使用场景 
> 在 TabooLib 中创建定时任务，无需手动注册
> 通过注解声明方式定义周期性执行的方法
> 实现插件功能的定时执行，如数据保存、状态更新等

## 注意事项 
> @Schedule 注解必须包含正确的参数，如 async、delay 和 period
> period 为 0 时表示任务只执行一次，大于 0 时表示周期性执行
> 被 @Schedule 注解标记的方法不应该有返回值依赖
> 该类由 TabooLib 自动注册和使用，不需要直接实例化
