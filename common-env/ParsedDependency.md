# ParsedDependency  
## 基本信息  
- 类名和包路径: taboolib.common.env.ParsedDependency  
- 基本用途: 解析依赖信息，表示一个运行时依赖的所有属性  
- 类型: 类  
- 所属模块: common-env  
---
## 类结构  
### 类内可被访问字段  
> value: String -> 依赖地址，格式为 <groupId>:<artifactId>[:<extension>[:<classifier>]]:<version>  
> test: String -> 测试类，用于检查依赖是否已存在  
> repository: String -> 仓库地址，留空默认使用阿里云中央仓库  
> transitive: boolean -> 是否进行依赖传递  
> ignoreOptional: boolean -> 忽略可选依赖  
> ignoreException: boolean -> 忽略加载异常  
> scopes: List<DependencyScope> -> 依赖范围  
> relocate: List<String> -> 依赖重定向规则  
> external: boolean -> 是否外部库（不会被扫到）  
  
### 类方法  
> ParsedDependency(value: String, test: String, repository: String, transitive: boolean, ignoreOptional: boolean, ignoreException: boolean, scopes: List<DependencyScope>, relocate: List<String>, external: boolean): ParsedDependency -> 构造函数  
> ParsedDependency(map: Map<String, Object>): ParsedDependency -> 从Map构造依赖信息  
> value(): String -> 获取依赖地址  
> test(): String -> 获取测试类  
> repository(): String -> 获取仓库地址  
> transitive(): boolean -> 是否进行依赖传递  
> ignoreOptional(): boolean -> 是否忽略可选依赖  
> ignoreException(): boolean -> 是否忽略加载异常  
> scopes(): List<DependencyScope> -> 获取依赖范围  
> relocate(): List<String> -> 获取依赖重定向规则  
> external(): boolean -> 是否外部库  
> toString(): String -> 获取字符串表示  
---
## 实现细节  
- 提供了完整的依赖信息解析和存储  
- 支持从Map构造，方便从注解属性转换  
---
## 使用场景  
> 在RuntimeEnvDependency中解析并处理依赖  
> 保存从RuntimeDependency注解中提取的依赖信息  
---
## 注意事项  
> relocate属性必须成对提供，表示从一个包路径到另一个包路径的映射  
> test属性可以使用感叹号(!)前缀避免在编译时重定向