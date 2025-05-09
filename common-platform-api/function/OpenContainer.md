# OpenContainer
## 基本信息 
- 类名和包路径: taboolib.common.platform.function.OpenContainer
- 基本用途: 提供访问跨平台开放接口容器的顶层函数
- 类型: Kotlin 文件，包含顶层函数
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段（文件级别）

### 公开静态方法 
> getOpenContainers(): List<OpenContainer> -> 获取当前服务端中运行的所有开放接口
> getOpenContainer(name: String): OpenContainer? -> 获取特定名称的开放接口

### 类内可被访问字段 
> 无类内可被访问字段（文件级别）

### 类方法
> 无类方法（文件级别）

## 实现细节
- 所有函数都是顶层函数，可以直接导入使用，无需通过类实例调用
- 内部通过 PlatformFactory.getService<PlatformOpenContainer>() 获取平台开放容器服务实例
- getOpenContainers 函数返回当前服务端中所有可用的开放接口列表
- getOpenContainer 函数通过名称查找特定的开放接口，如果不存在则返回 null
- 开放接口（OpenContainer）是一种跨平台的通信机制，允许不同插件之间共享功能

## 使用场景 
> 获取服务端中所有可用的开放接口
> 查找并使用特定名称的开放接口
> 实现插件间的功能共享和通信
> 访问其他插件提供的 API 功能

## 注意事项 
> getOpenContainer 函数在找不到指定名称的接口时返回 null，调用时需要处理空值情况
> 开放接口的可用性取决于当前服务端环境和已加载的插件
> 使用开放接口时应考虑版本兼容性和接口稳定性
> 这些函数依赖于 PlatformOpenContainer 服务，确保在适当的生命周期阶段调用