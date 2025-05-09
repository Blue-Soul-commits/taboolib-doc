# YamlCommentLoader
## 基本信息
- 类名和包路径: taboolib.module.configuration.YamlCommentLoader
- 基本用途: 处理 YAML 文件中的注释，包括加载、调整和保存注释
- 类型: 工具类
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> yamlDumperOptions: DumperOptions -> YAML 转储选项
> yamlLoaderOptions: LoaderOptions -> YAML 加载选项
> constructor: YamlConstructor -> YAML 构造器
> representer: YamlRepresenter -> YAML 表示器
> yaml: Yaml -> YAML 解析器实例

### 类方法
> YamlCommentLoader(yamlDumperOptions: DumperOptions, yamlLoaderOptions: LoaderOptions, constructor: YamlConstructor, representer: YamlRepresenter, yaml: Yaml) -> 初始化 YamlCommentLoader 实例
> adjustNodeComments(node: MappingNode): void -> 调整节点注释，将头部注释分配给根节点和第一个键
> fromNodeTree(input: MappingNode, section: ConfigurationSection): void -> 将 YAML 节点树转换为 ConfigurationSection，保留注释
> toNodeTree(section: ConfigurationSection): MappingNode -> 将 ConfigurationSection 转换为 YAML 节点树，保留注释
> getCommentLines(comments: List<CommentLine>): List<String> -> 将 CommentLine 列表转换为字符串列表
> getCommentLines(comments: List<String>, commentType: CommentType): List<CommentLine> -> 将字符串列表转换为 CommentLine 列表

## 实现细节
- 负责在 YAML 文件的读写过程中保留和处理注释信息
- 使用 SnakeYAML 库的注释支持功能，处理块注释和内联注释
- 在 adjustNodeComments 方法中，将文件头部注释与第一个键的注释分离
- 在 fromNodeTree 方法中，递归地将 YAML 节点树转换为 ConfigurationSection，同时保留注释
- 在 toNodeTree 方法中，递归地将 ConfigurationSection 转换为 YAML 节点树，同时应用注释
- 提供工具方法在 SnakeYAML 的 CommentLine 和 TabooLib 的字符串注释之间进行转换
- 目前不完全支持内联注释，内联注释会被转换为普通注释

## 使用场景
> 在 YamlParser 中用于从 YAML 文件加载配置时保留注释
> 在 YamlWriter 中用于将配置保存为 YAML 文件时保留注释
> 支持 ConfigurationSection 接口中的注释相关方法，如 getComment、setComment 等
> 与 BukkitYaml、YamlConstructor 和 YamlRepresenter 配合使用，构成 TabooLib 的 YAML 处理系统
> 使用 withComment 扩展函数为配置值添加注释

## 注意事项
> 依赖于 SnakeYAML 2.2 版本的注释支持功能
> 当前版本不完全支持内联注释，相关代码被注释掉
> 在处理注释时，空行被表示为 null 值的注释
> 在转换注释时，会自动处理注释前的空格
> 主要设计用于与 TabooLib 的配置系统一起使用，不建议单独使用
