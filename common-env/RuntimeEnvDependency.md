# RuntimeEnvDependency  
## 基本信息  
- 类名和包路径: taboolib.common.env.RuntimeEnvDependency  
- 基本用途: 运行时依赖管理，负责加载和管理Maven依赖  
- 类型: 类  
- 所属模块: common-env  
---
## 类结构  
### 类内可被访问字段  
> defaultLibrary: String -> 默认库目录  
> defaultRepositoryCentral: String -> 默认中央仓库地址  
  
### 公开静态字段  
> isAetherFound: boolean -> 是否找到Aether库  
  
### 类方法  
> getDependency(clazz: ReflexClass): List<ParsedDependency> -> 获取类上声明的依赖列表  
> loadDependency(clazz: ReflexClass): int -> 加载类上声明的依赖，返回加载的依赖数量  
> loadDependency(url: String): void -> 加载指定URL的依赖  
> loadDependency(url: String, repository: String): void -> 从指定仓库加载依赖  
> loadDependency(url: String, relocation: List<JarRelocation>): void -> 加载依赖并应用重定向  
> loadDependency(url: String, transitive: boolean, relocation: List<JarRelocation>): void -> 加载依赖，控制是否传递依赖  
> loadDependency(url: String, baseDir: File): void -> 加载依赖到指定目录  
> loadDependency(url: String, baseDir: File, repository: String): void -> 从指定仓库加载依赖到指定目录  
> loadDependency(url: String, baseDir: File, relocation: List<JarRelocation>, repository: String, ignoreOptional: boolean, ignoreException: boolean, transitive: boolean, scope: List<DependencyScope>): void -> 完整参数的依赖加载方法  
> loadDependency(url: String, baseDir: File, relocation: List<JarRelocation>, repository: String, ignoreOptional: boolean, ignoreException: boolean, transitive: boolean, scope: List<DependencyScope>, external: boolean): void -> 完整参数的依赖加载方法，增加external参数  
> loadDependencyLegacy(...): void -> 使用Legacy方式加载依赖  
> loadFromLocalFile(url: URL): void -> 从本地文件加载依赖配置  
> test(path: String): boolean -> 测试类是否存在  
> find(object: JsonObject, key: String, def: String): String -> 从JSON对象获取字符串值，带默认值  
> find(object: JsonObject, key: String): boolean -> 从JSON对象获取布尔值  
> array(object: JsonObject, key: String): JsonArray -> 从JSON对象获取JSON数组  
---
## 实现细节  
- 支持使用Aether库或Legacy方式加载依赖  
- 自动检测环境决定使用哪种依赖加载方式  
- 支持依赖传递、可选依赖控制、异常处理  
- 支持JAR包重定向以避免类冲突  
- 提供从本地JSON文件加载依赖配置的能力  
---
## 使用场景  
> 加载类上声明的RuntimeDependency注解  
> 从Maven仓库下载和管理依赖  
> 处理依赖传递和类路径冲突  
---
## 注意事项  
> Mohist服务端直接不使用Aether加载依赖  
> 当服务端版本在1.17+时，可借助服务端自带的Aether库完成依赖下载  
> 支持用户对仓库源进行替换