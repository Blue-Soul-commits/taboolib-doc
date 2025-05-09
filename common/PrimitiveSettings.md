# PrimitiveSettings  
## 基本信息  
- 类名和包路径: taboolib.common.PrimitiveSettings  
- 基本用途: 提供 TabooLib 的配置信息和运行参数  
- 类型: 配置类  
- 所属模块: Common  
---
## 类结构  
  
### 公开静态字段  
> ID: String -> TabooLib 的标识符  
> RUNTIME_PROPERTIES: Properties -> 运行时参数  
> VERSION_PROPERTIES: Properties -> 版本信息  
> KOTLIN_VERSION: String -> Kotlin 版本  
> KOTLIN_COROUTINES_VERSION: String -> Kotlin 协程版本  
> TABOOLIB_VERSION: String -> TabooLib 版本  
> SKIP_KOTLIN_RELOCATE: boolean -> 是否跳过 Kotlin 重定向  
> SKIP_TABOOLIB_RELOCATE: boolean -> 是否跳过 TabooLib 重定向  
> IS_DEV_MODE: boolean -> 是否处于开发模式  
> IS_DEBUG_MODE: boolean -> 是否处于调试模式  
> IS_FORCE_DOWNLOAD_IN_DEV_MODE: boolean -> 是否在开发模式下强制下载依赖  
> REPO_CENTRAL: String -> 中央仓库地址  
> REPO_TABOOLIB: String -> TabooLib 仓库地址  
> REPO_REFLEX: String -> Reflex 仓库地址  
> FILE_LIBS: String -> 依赖库保存路径  
> FILE_ASSETS: String -> 资源文件保存路径  
> IS_ISOLATED_MODE: boolean -> 是否启用完全隔离模式  
> INSTALL_MODULES: String[] -> 要加载的模块列表  
  
### 公开静态方法  
> formatVersion(str: String): String -> 格式化版本号，移除分隔符  
> getRelocatedKotlinVersion(): String -> 获取重定向后的 Kotlin 版本标识  
> getRelocatedKotlinCoroutinesVersion(): String -> 获取重定向后的 Kotlin 协程版本标识  
  
### 类内可被访问字段  
(无额外字段)  
  
### 类方法  
> getProperties(name: String, allowGlobal: boolean): Properties -> 获取配置文件  
---
## 实现细节  
- 从 META-INF/taboolib/env.properties 和 version.properties 加载配置  
- 支持从系统属性和全局配置文件覆盖设置  
- 提供重定向相关的版本格式化功能  
---
## 使用场景  
> 获取仓库地址和文件路径配置  
> 确定当前运行模式（开发、调试、隔离）  
> 获取 Kotlin 和 TabooLib 版本信息  
---
## 注意事项  
> 配置优先级：系统属性 > 全局配置文件 > 插件内部配置  
> 开发模式下自动启用调试模式  
> 隔离模式需要明确配置开启  