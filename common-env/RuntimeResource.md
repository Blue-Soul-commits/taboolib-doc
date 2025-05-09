# RuntimeResource  
## 基本信息  
- 类名和包路径: taboolib.common.env.RuntimeResource  
- 基本用途: 用于声明运行时需要加载的资源  
- 类型: 注解  
- 所属模块: common-env  
---
## 类结构  
### 公开静态方法  
> value(): String -> 资源地址  
> hash(): String -> 实际资源的哈希值，采用SHA-1算法  
> name(): String -> 资源名称，留空使用哈希值作为名称，默认为空  
> tag(): String -> 标签（标识用），默认为空  
> zip(): boolean -> 是否为压缩文件，默认为false  
---
## 实现细节  
- 目标为ElementType.TYPE，即可以应用于类、接口、枚举等类型  
- 保留策略为RetentionPolicy.RUNTIME，即在运行时可通过反射获取  
- 可重复使用（@Repeatable(RuntimeResources.class)）  
---
## 使用场景  
> 在类上声明运行时需要加载的资源  
> 自动下载和管理所需的资源文件  
---
## 注意事项  
> 启用zip选项时，将从value() + ".zip"下载文件  
> 无论是否启用zip选项，哈希值判断都依据".zip"内的实际资源，而非".zip"本身