# IO
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.IO
- 基本用途: 提供跨平台输入输出操作的顶层函数集合，包括日志打印和资源文件管理
- 类型: Kotlin 文件，包含顶层函数
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段（文件级别）

### 公开静态方法 
> server<T>(): T -> 获取平台特定的控制台对象
> debug(vararg message: Any?): Unit -> 打印调试信息，仅在调试模式下有效
> info(vararg message: Any?): Unit -> 打印普通日志信息
> severe(vararg message: Any?): Unit -> 打印错误日志信息
> warning(vararg message: Any?): Unit -> 打印警告日志信息
> releaseResourceFile(source: String, replace: Boolean = false, target: String = source): File -> 释放插件内的特定资源文件
> releaseResourceFolder(prefix: String, replace: Boolean = false): Unit -> 释放插件内特定目录下的所有资源文件
> getJarFile(): File -> 获取当前插件的 Jar 文件对象
> getDataFolder(): File -> 获取当前插件的配置文件目录
> getPlatformData(): Map<String, Any> -> 获取当前平台的信息，用于统计

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有函数都是顶层函数，可以直接导入使用，无需通过类实例调用
- 内部通过 PlatformFactory.getService<PlatformIO>() 获取平台 IO 服务实例
- debug 函数只在调试模式（isDebugMode 为 true）下输出信息
- 日志函数（info、severe、warning）支持多个参数，会依次输出
- releaseResourceFile 函数用于从插件 JAR 中提取单个资源文件到插件数据目录
- releaseResourceFolder 函数用于从插件 JAR 中提取指定前缀的所有资源文件
- getDataFolder 返回的目录可能不存在，需要手动创建

## 使用场景 
> 输出各种级别的日志信息
> 从插件 JAR 中提取配置文件和资源文件
> 获取插件数据目录和 JAR 文件
> 获取平台特定的控制台对象

## 注意事项 
> debug 函数只在调试模式下输出信息，可用于开发调试
> getDataFolder 返回的目录可能不存在，使用前应检查或调用 mkdirs 方法创建
> releaseResourceFile 和 releaseResourceFolder 函数默认不会覆盖已存在的文件
> server 函数需要指定正确的泛型类型，对应平台特定的控制台类型
