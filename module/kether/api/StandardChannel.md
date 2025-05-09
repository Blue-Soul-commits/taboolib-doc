# StandardChannel

## 基本信息
- 类名和包路径: taboolib.module.kether.StandardChannel
- 基本用途: Kether脚本引擎的远程通信通道，实现跨容器的脚本组件交互
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> REMOTE_RESOLVE: String -> 远程解析动作的通道名称常量
> REMOTE_CREATE_FLAME: String -> 远程创建执行帧的通道名称常量
> REMOTE_CREATE_EXIT_STATUS: String -> 远程创建退出状态的通道名称常量
> REMOTE_CREATE_PARSED_ACTION: String -> 远程创建已解析动作的通道名称常量
> REMOTE_ADD_ACTION: String -> 远程添加动作的通道名称常量
> REMOTE_REMOVE_ACTION: String -> 远程移除动作的通道名称常量
> REMOTE_ADD_PROPERTY: String -> 远程添加属性的通道名称常量
> REMOTE_REMOVE_PROPERTY: String -> 远程移除属性的通道名称常量

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> call(name: String, data: Array<Any>): OpenResult -> 实现OpenListener接口的方法，处理远程调用请求

## 实现细节
- StandardChannel实现了OpenListener接口，提供跨容器的通信机制
- 使用@Awake、@Inject和@PlatformSide注解标记为Bukkit平台上的自动注入监听器
- 通过call方法处理不同类型的远程调用请求，根据name参数区分操作类型
- 支持多种远程操作，包括解析动作、创建执行帧、管理动作和属性等
- 使用getOpenContainer获取远程容器实例，实现跨容器通信
- 对类名处理时支持使用"@"前缀表示相对于当前groupId的类名

## 使用场景
> 跨插件或模块间的Kether脚本组件共享
> 在不同的ClassLoader环境下实现脚本解析和执行
> 允许一个插件注册的动作被其他插件使用
> 实现插件间的脚本属性共享和管理

## 注意事项
> 仅在Bukkit平台上可用，由@PlatformSide(Platform.BUKKIT)指定
> 远程调用需要正确传递容器标识符和相关数据
> 类名处理支持"@"前缀简写，会自动补全groupId
> 对ClassNotFoundException等异常进行了处理，返回失败结果而非抛出异常
> 使用了反射获取属性，可能存在兼容性风险
