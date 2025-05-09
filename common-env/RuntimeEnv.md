# RuntimeEnv  
## 基本信息  
- 类名和包路径: taboolib.common.env.RuntimeEnv  
- 基本用途: 运行时环境管理，提供依赖和资源的加载能力  
- 类型: 类  
- 所属模块: common-env  
---
## 类结构  
### 公开静态字段  
> KOTLIN_ID: String -> Kotlin包的标识符  
> KOTLIN_COROUTINES_ID: String -> Kotlin协程包的标识符  
> ENV: RuntimeEnv -> RuntimeEnv的全局实例  
> ENV_ASSETS: RuntimeEnvAssets -> RuntimeEnvAssets的全局实例  
> ENV_DEPENDENCY: RuntimeEnvDependency -> RuntimeEnvDependency的全局实例  
  
### 公开静态方法  
> init(): void -> 初始化运行时环境，由extra.properties调用，用于初始化Kotlin环境  
  
### 类方法  
> inject(clazz: ReflexClass): int -> 注入依赖和资源，返回加载的依赖和资源总数  
---
## 实现细节  
- 负责初始化和管理运行时环境  
- 自动加载Kotlin和Kotlin协程的依赖  
- 支持从本地文件加载依赖定义  
- 提供依赖和资源的统一注入接口  
---
## 使用场景  
> 初始化TabooLib运行时环境  
> 加载类上声明的运行时依赖和资源  
---
## 注意事项  
> 在非隔离模式下会启用重定向和环境检查  
> 在隔离模式下不会检查Kotlin环境，只要定义版本必定加载