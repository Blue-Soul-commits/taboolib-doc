# RuntimeDependency  
## 基本信息  
- 类名和包路径: taboolib.common.env.RuntimeDependency  
- 基本用途: 用于声明运行时需要加载的依赖  
- 类型: 注解  
- 所属模块: common-env  
---
## 类结构  
### 公开静态方法  
> value(): String -> 依赖地址，格式为 <groupId>:<artifactId>[:<extension>[:<classifier>]]:<version>  
> test(): String -> 测试类，用于检查依赖是否已存在，默认为空  
> repository(): String -> 仓库地址，留空默认使用阿里云中央仓库，默认为空  
> transitive(): boolean -> 是否进行依赖传递，默认为true  
> ignoreOptional(): boolean -> 忽略可选依赖，默认为true  
> ignoreException(): boolean -> 忽略加载异常，默认为false  
> scopes(): DependencyScope[] -> 依赖范围，默认为{DependencyScope.RUNTIME, DependencyScope.COMPILE}  
> relocate(): String[] -> 依赖重定向规则，默认为空数组  
> external(): boolean -> 是否外部库（不会被扫到），默认为true  
---
## 实现细节  
- 目标为ElementType.TYPE，即可以应用于类、接口、枚举等类型  
- 保留策略为RetentionPolicy.RUNTIME，即在运行时可通过反射获取  
- 可重复使用（@Repeatable(RuntimeDependencies.class)）  
---
## 使用场景  
> 在类上声明运行时需要加载的Maven依赖  
> 自动检测并加载所需的依赖项  
---
## 注意事项  
> test参数可以使用感叹号(!)前缀避免在编译时重定向  
> relocate参数必须成对提供，表示从一个包路径到另一个包路径的映射