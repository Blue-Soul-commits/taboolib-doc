# PlatformService
## 基本信息 
- 类名和包路径: taboolib.common.platform.PlatformService
- 基本用途: 标记作为平台服务的类，用于跨平台功能实现
- 类型: Kotlin 注解类
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> 无类内可被访问字段

### 类方法
> 无类方法（注解类）

## 实现细节
- 使用 @Target(AnnotationTarget.CLASS) 标记，表示该注解只能应用于类
- 使用 @Retention(AnnotationRetention.RUNTIME) 标记，表示该注解在运行时可通过反射获取
- 作为 TabooLib 平台抽象层的一部分，用于标识平台特定服务的实现类
- 通常与 @PlatformSide 注解配合使用，指定服务适用的平台

## 使用场景 
> 标记平台特定功能的实现类，如 Bukkit、Bungee、Velocity 等平台的特定服务
> 实现跨平台功能时，定义各平台的具体实现
> 作为 TabooLib 服务注册系统的一部分，自动注册平台服务

## 注意事项 
> 被此注解标记的类通常需要实现某个通用接口或继承某个抽象类
> 在运行时，TabooLib 会根据当前运行平台选择合适的服务实现
> 通常需要配合 @PlatformSide 注解使用，明确指定服务适用的平台
> 该注解主要用于 TabooLib 内部的平台抽象层，普通开发者较少直接使用
