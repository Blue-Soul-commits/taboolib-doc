# ClassAppender
- 基本信息
- 类名和包路径: taboolib.common.ClassAppender
- 基本用途: 提供动态加载类和库的功能
- 类型: 工具类
- 所属模块: Common
---
## 类结构
### 公开静态字段
> lookup: MethodHandles.Lookup -> 反射查找器
> unsafe: Unsafe -> 用于底层操作的 Unsafe 实例
> callbacks: List -> 回调函数列表

### 公开静态方法
> addPath(path: Path, isIsolated: boolean, isExternal: boolean): ClassLoader -> 加载文件到 ClassLoader
> getClassLoader(): ClassLoader -> 获取 addPath 函数所使用的 ClassLoader
> isExists(path: String): boolean -> 判断类是否存在
> registerCallback(callback: Callback): void -> 注册回调函数

### 类内可被访问字段
> (无额外字段)

### 类方法
> (无实例方法)
---
## 实现细节
> 使用 sun.misc.Unsafe 进行底层操作，获取非公开的 MethodHandles.Lookup
> 支持向不同类型的 ClassLoader 添加路径：Application、Hybrid、Bukkit
>提供回调接口，允许在加载类时执行自定义逻辑
---
## 使用场景
> 加载外部库和依赖
> 在运行时动态添加类和资源
> 支持隔离加载或共享加载
---
## 注意事项
> 依赖 sun.misc.Unsafe，可能在未来的 JDK 版本中不兼容
> 如果 Unsafe lookup 没有找到，会导致 TabooLib 无法正常工作