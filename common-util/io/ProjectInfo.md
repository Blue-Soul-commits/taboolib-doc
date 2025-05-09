# EnvironmentVariables

## 基本信息
- 类名和包路径: taboolib.common.io (属性文件)
- 基本用途: 提供TabooLib环境相关的常量和属性
- 类型: Kotlin属性集合
- 所属模块: common-io

## 类结构
### 公开静态字段
> isDebugMode: Boolean -> 是否为调试模式
> isDevelopmentMode: Boolean -> 是否为开发模式
> taboolibId: String -> "taboolib"字符串常量
> groupId: String -> 当前项目的组名
> taboolibPath: String -> 完整的TabooLib包路径
> Class<*>.groupId: String -> 获取类所属的组名

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- `isDebugMode`和`isDevelopmentMode`直接从PrimitiveSettings获取配置
- `taboolibId`使用字符数组构建，避免字符串直接出现在代码中
- `groupId`默认从"taboolib"字符串解析，也支持从系统属性获取
- `taboolibPath`组合groupId和taboolibId生成完整包路径
- `Class<*>.groupId`扩展属性从类名中提取组名部分

## 使用场景
> 需要判断当前运行环境是否为开发模式
> 需要获取当前项目的组名或包路径
> 需要从类名中提取组名信息

## 注意事项
> `groupId`属性有自定义getter，可能与直接字段访问行为不同
> 这些属性依赖于PrimitiveSettings的配置
> 在不同环境中，这些属性可能返回不同的值
