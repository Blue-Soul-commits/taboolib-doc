# RuntimeEnvAssets  
## 基本信息  
- 类名和包路径: taboolib.common.env.RuntimeEnvAssets  
- 基本用途: 运行时资源管理，负责加载和管理资源文件  
- 类型: 类  
- 所属模块: common-env  
---
## 类结构  
### 类内可被访问字段  
> defaultAssets: String -> 默认资源目录  
  
### 类方法  
> getAssets(clazz: ReflexClass): List<ParsedResource> -> 获取类上声明的资源列表  
> loadAssets(clazz: ReflexClass): int -> 加载类上声明的资源，返回加载的资源数量  
> loadAssets(name: String, hash: String, url: String, zip: boolean): void -> 下载资源文件到assets目录  
---
## 实现细节  
- 从类上获取RuntimeResource和RuntimeResources注解  
- 解析注解信息为ParsedResource对象  
- 支持下载普通资源和压缩资源  
- 使用SHA-1哈希验证资源完整性  
---
## 使用场景  
> 下载和管理插件需要的资源文件  
> 处理类上声明的RuntimeResource注解  
---
## 注意事项  
> 资源名为空时，使用哈希值作为名称  
> 启用zip选项时，将从url + ".zip"下载文件并解压