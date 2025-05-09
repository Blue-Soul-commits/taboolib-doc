# IsolatedClassLoader  
## 基本信息  
- 类名和包路径: taboolib.common.classloader.IsolatedClassLoader  
- 基本用途: 提供隔离的类加载环境  
- 类型: 类加载器  
- 所属模块: Common  
---
## 类结构  
  
### 公开静态字段  
> INSTANCE: IsolatedClassLoader -> 当前项目正在使用的加载器  
  
### 公开静态方法  
> init(clazz: Class<?>): void -> 初始化隔离类加载器  
  
### 类内可被访问字段  
> excludedClasses: Set<String> -> 排除的类列表  
> excludedPackages: Set<String> -> 排除的包列表  
  
### 类方法  
> addURL(url: URL): void -> 添加 URL 到类加载器  
> loadClass(name: String, resolve: boolean): Class<?> -> 加载类  
> loadClass(name: String, resolve: boolean, checkParents: boolean): Class<?> -> 加载类（可控制是否检查父级）  
> addExcludedClass(name: String): void -> 添加排除类  
> addExcludedClasses(names: Collection<String>): void -> 批量添加排除类  
> addExcludedPackage(name: String): void -> 添加排除包  
> addExcludedPackages(names: Collection<String>): void -> 批量添加排除包  
---
## 实现细节  
- 继承自 URLClassLoader，提供类隔离功能  
- 默认排除 Java 核心类和关键 TabooLib 类  
- 通过 ServiceLoader 加载配置实现可扩展的类排除机制  
- 优先加载自身类，防止访问其他插件的类  
---
## 使用场景  
> 实现插件之间的类隔离  
> 防止不同版本依赖冲突  
> 隔离加载 TabooLib 核心库  
---
## 注意事项  
> 需要正确配置排除类，否则可能导致跨类加载器访问问题  
> 排除的类会委托给父类加载器加载  