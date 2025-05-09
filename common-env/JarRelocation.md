# JarRelocation  
## 基本信息  
- 类名和包路径: taboolib.common.env.JarRelocation  
- 基本用途: 提供JAR包重定向功能，用于避免类名冲突  
- 类型: 类  
- 所属模块: common-env  
---
## 类结构  
### 类内可被访问字段  
> pattern: String -> 需要重定向的包路径模式  
> relocatedPattern: String -> 重定向后的包路径模式  
  
### 类方法  
> JarRelocation(pattern: String, relocatedPattern: String): JarRelocation -> 构造函数，创建一个JAR重定向规则  
> getPattern(): String -> 获取原始包路径模式  
> getRelocatedPattern(): String -> 获取重定向后的包路径模式  
> toRelocation(): Relocation -> 转换为me.lucko.jarrelocator包中的Relocation对象  
> equals(o: Object): boolean -> 比较两个JarRelocation对象是否相等  
> hashCode(): int -> 获取哈希码  
---
## 实现细节  
- 提供了在JAR文件中重定位包的功能  
- 利用me.lucko.jarrelocator库实现实际的重定向操作  
---
## 使用场景  
> 在依赖加载时防止类路径冲突  
> 在RuntimeDependency中使用relocate属性指定重定向规则  
---
## 注意事项  
> 重定向规则通常成对使用，表示从一个包路径到另一个包路径的映射