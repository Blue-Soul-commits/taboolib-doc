# DependencyScope  
## 基本信息  
- 类名和包路径: taboolib.common.env.DependencyScope  
- 基本用途: 定义依赖项的作用域，指定依赖项如何在运行时被解析和使用  
- 类型: 枚举  
- 所属模块: common-env  
---
## 类结构  
### 公开静态字段  
> COMPILE: DependencyScope -> 依赖项在编译代码时需要，因此它将在运行时解析依赖项时下载  
> PROVIDED: DependencyScope -> 依赖项由运行时环境提供，因此在运行时解析依赖项时无需下载  
> RUNTIME: DependencyScope -> 依赖项在应用程序运行时需要，因此它将在运行时解析依赖项时下载  
> TEST: DependencyScope -> 依赖项在编译和运行单元测试时需要，因此在运行时解析依赖项时无需下载  
> SYSTEM: DependencyScope -> 依赖项应该已经在系统上，因此在运行时解析依赖项时无需下载  
> IMPORT: DependencyScope -> 依赖项实际上只是一个 pom 而不是一个 jar，因此我们不需要下载它  
---
## 实现细节  
- 定义了六种不同的依赖作用域类型  
- 用于确定依赖项在运行时是否需要下载  
---
## 使用场景  
> 在RuntimeDependency注解中指定依赖项的作用域  
> 在依赖解析流程中确定依赖项如何被处理  
---
## 注意事项  
> 默认情况下，RuntimeDependency使用RUNTIME和COMPILE作用域