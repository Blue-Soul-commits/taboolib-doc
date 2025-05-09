# AetherResolver  
## 基本信息  
- 类名和包路径: taboolib.common.env.aether.AetherResolver  
- 基本用途: 使用Aether库解析和加载Maven依赖  
- 类型: 类  
- 所属模块: common-env  
---
## 类结构  
### 公开静态字段  
> resolverMap: Map<String, AetherResolver> -> AetherResolver实例映射  
> injectedDependencies: Set<String> -> 已注入的依赖路径集合  
  
### 类内可被访问字段  
> repository: RepositorySystem -> 仓库系统  
> session: DefaultRepositorySystemSession -> 仓库会话  
> repositories: List<RemoteRepository> -> 远程仓库列表  
  
### 公开静态方法  
> of(repository: String): AetherResolver -> 获取或创建指定仓库的AetherResolver实例  
> inject(file: File, relocation: List<JarRelocation>, isExternal: boolean): ClassLoader -> 注入依赖文件，应用重定向规则  
  
### 类方法  
> AetherResolver(repo: String): AetherResolver -> 构造函数，创建指定仓库的解析器  
> resolve(library: String, scope: List<DependencyScope>, isTransitive: boolean, ignoreOptional: boolean): List<File> -> 解析依赖，返回依赖文件列表  
> getDependencyRequest(dependency: Dependency, scope: List<DependencyScope>, isTransitive: boolean, ignoreOptional: boolean): DependencyRequest -> 获取依赖请求  
---
## 实现细节  
- 使用Eclipse Aether库解析Maven依赖  
- 支持依赖传递控制和可选依赖控制  
- 提供JAR包重定向功能以避免类冲突  
- 使用缓存避免重复加载依赖  
---
## 使用场景  
> 在1.17+服务端环境中解析和加载Maven依赖  
> 由RuntimeEnvDependency调用，加载RuntimeDependency注解声明的依赖  
---
## 注意事项  
> 依赖重定向时创建临时文件进行处理  
> 通过检查injectedDependencies避免重复加载依赖