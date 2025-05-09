# ParsedResource  
## 基本信息  
- 类名和包路径: taboolib.common.env.ParsedResource  
- 基本用途: 解析资源信息，表示一个运行时资源的所有属性  
- 类型: 类  
- 所属模块: common-env  
---
## 类结构  
### 类内可被访问字段  
> value: String -> 资源地址  
> hash: String -> 实际资源的哈希值，采用SHA-1算法  
> name: String -> 资源名称，留空使用哈希值作为名称  
> tag: String -> 标签（标识用）  
> zip: boolean -> 是否为压缩文件  
  
### 类方法  
> ParsedResource(annotation: Map<String, Object>): ParsedResource -> 从Map构造资源信息  
> value(): String -> 获取资源地址  
> hash(): String -> 获取哈希值  
> name(): String -> 获取资源名称  
> tag(): String -> 获取标签  
> zip(): Boolean -> 是否为压缩文件  
> toString(): String -> 获取字符串表示  
---
## 实现细节  
- 提供了完整的资源信息解析和存储  
- 支持从注解属性转换为资源对象  
---
## 使用场景  
> 在RuntimeEnvAssets中解析并处理资源  
> 保存从RuntimeResource注解中提取的资源信息  
---
## 注意事项  
> 启用zip选项时，将从value() + ".zip"下载文件  
> 无论是否启用zip选项，哈希值判断都依据".zip"内的实际资源，而非".zip"本身