# Plugin
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.Plugin
- 基本用途: 提供跨平台插件信息和状态的顶层属性
- 类型: Kotlin 文件，包含顶层属性
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> pluginId: String -> 获取当前插件的名称
> pluginVersion: String -> 获取当前插件的版本
> isPrimaryThread: Boolean -> 检查当前是否在主线程中运行

### 公开静态方法 
> 无公开静态方法（文件级别）

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有属性都是顶层属性，可以直接导入使用，无需通过类实例访问
- 内部通过 PlatformFactory.getService<PlatformIO>() 获取平台 IO 服务实例
- 使用 inline 修饰符优化属性访问性能，避免额外的函数调用开销
- pluginId 属性返回当前插件的名称标识符
- pluginVersion 属性返回当前插件的版本字符串
- isPrimaryThread 属性检查当前代码是否在服务器主线程中执行

## 使用场景 
> 获取当前插件的基本信息，如名称和版本
> 在日志和消息中显示插件信息
> 检查代码是否在主线程中运行，避免线程安全问题
> 在配置文件和数据存储中使用插件标识符

## 注意事项 
> 这些属性依赖于 PlatformIO 服务，确保在适当的生命周期阶段访问
> isPrimaryThread 属性对于线程安全检查非常重要，特别是在操作游戏主线程对象时
> 在异步任务中访问主线程对象前，应先检查 isPrimaryThread 属性
> 插件名称和版本通常从插件配置文件（如 plugin.yml）中读取
