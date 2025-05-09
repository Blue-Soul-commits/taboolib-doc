# Common
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.Common
- 基本用途: 提供跨平台通用功能的顶层属性和函数集合
- 类型: Kotlin 文件，包含顶层属性和函数
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> runningPlatform: Platform -> 当前运行平台，对应 Platform.CURRENT 的值

### 公开静态方法 
> disablePlugin(): Unit -> 停用插件
> registerLifeCycleTask(lifeCycle: LifeCycle = LifeCycle.ENABLE, priority: Int = 0, runnable: Runnable): Unit -> 注册生命周期任务
> postpone(lifeCycle: LifeCycle = LifeCycle.ENABLE, priority: Int = 0, runnable: Runnable): Unit -> 已废弃，使用 registerLifeCycleTask 替代
> implementation<T>(): T -> 获取指定类型的实现类
> implementationOrNull<T>(): T? -> 获取指定类型的实现类，可能为空
> implementations<T>(): T -> 已废弃，使用 implementation 替代

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有属性和函数都是顶层定义，可以直接导入使用，无需通过类实例调用
- runningPlatform 属性提供对当前运行平台的快速访问
- disablePlugin 函数通过调用 TabooLib.setStopped(true) 来停用插件
- registerLifeCycleTask 函数用于在指定生命周期阶段执行任务，支持优先级设置
- implementation 和 implementationOrNull 函数是 PlatformFactory.getAPI 和 getAPIOrNull 的便捷包装
- 包含两个已废弃的函数：postpone 和 implementations，它们分别被 registerLifeCycleTask 和 implementation 替代

## 使用场景 
> 检查当前运行平台
> 在特定生命周期阶段执行任务
> 获取跨平台 API 的实现类
> 在特殊情况下停用插件

## 注意事项 
> registerLifeCycleTask 如果指定的生命周期已经过去，任务会立即执行
> implementation 函数在找不到实现类时会抛出异常，对于可能不存在的实现类应使用 implementationOrNull
> disablePlugin 函数应谨慎使用，通常只在严重错误或用户请求时调用
> 避免使用已废弃的 postpone 和 implementations 函数
