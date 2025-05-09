# Comments
## 基本信息
- 类名和包路径: taboolib.module.configuration.util.Comments
- 基本用途: 提供为配置值添加注释的便捷工具
- 类型: 文件 (包含扩展函数和数据类)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> Any.withComment(comment: String): Commented -> 为任意值添加单行注释
> Any.withComment(comment: List<String>): CommentedList -> 为任意值添加多行注释

### 类内可被访问字段
#### Commented 类
> value: Any? -> 原始值
> comment: String -> 注释内容

#### CommentedList 类
> value: Any? -> 原始值
> comment: List<String> -> 多行注释内容

### 类方法
> 无

## 实现细节
- 提供了两个中缀扩展函数 (infix function)，可以使用更自然的语法为值添加注释
- Commented 类用于存储带有单行注释的值
- CommentedList 类用于存储带有多行注释的值
- 这些类和函数与 ConfigSection 的 set 方法集成，在设置值时会处理注释

## 使用场景
> 在配置文件中为配置项添加说明性注释
> 创建带有详细文档的默认配置文件
> 在生成配置模板时添加使用说明
> 为复杂配置结构添加分节注释

## 注意事项
> 注释功能仅在支持注释的配置格式中有效，如 YAML 和 TOML
> 在 JSON 等不支持注释的格式中，注释信息会被忽略
> 注释会在配置保存时写入文件，但不会影响值的读取
> 使用 withComment 是添加注释的推荐方式，比直接使用 setComment 更简洁
