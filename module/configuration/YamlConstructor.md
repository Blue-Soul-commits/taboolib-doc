# YamlConstructor
## 基本信息
- 类名和包路径: taboolib.library.configuration.YamlConstructor
- 基本用途: 自定义 YAML 构造过程，将 YAML 节点转换为 Java 对象
- 类型: 工具类
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 公开方法
> YamlConstructor(loaderOptions: LoaderOptions) -> 初始化 YamlConstructor 实例，并注册自定义对象构造器
> flattenMapping(node: MappingNode): void -> 重写父类方法，用于扁平化映射节点
> construct(node: Node): Object -> 构造给定节点的对象，返回构造的对象，可能为 null

### 内部类
> ConstructCustomObject extends ConstructYamlMap -> 自定义对象构造器，用于处理 YAML 映射节点
>> construct(node: Node): Object -> 构造给定节点的对象，如果节点是两步构造则抛出异常
>> construct2ndStep(node: Node, object: Object): void -> 执行对象构造的第二步，抛出异常以禁止引用映射结构

## 实现细节
- 继承自 SnakeYAML 的 SafeConstructor 类，该类提供了安全的 YAML 解析功能
- 在构造函数中，将 Tag.MAP 标签与自定义的 ConstructCustomObject 构造器关联
- ConstructCustomObject 内部类重写了 construct 方法，禁止使用两步构造过程
- 重写 flattenMapping 方法，用于处理嵌套的映射结构
- 提供 construct 方法，作为 constructObject 方法的公开包装器
- 与 YamlRepresenter 和 BukkitYaml 配合使用，共同构成 TabooLib 的 YAML 处理系统

## 使用场景
> 在 TabooLib 的配置系统中作为 YAML 解析的核心组件
> 在 YamlParser 和 YamlCommentLoader 中被实例化，用于将 YAML 节点转换为 Java 对象
> 处理配置文件中的复杂数据结构，如映射和列表
> 与 ConfigurationSection 接口配合，支持配置系统的数据访问

## 注意事项
> 禁止使用引用映射结构，如果遇到会抛出 YAMLException
> 依赖于 SnakeYAML 库，TabooLib 通过 RuntimeDependency 注解确保正确的版本被加载
> 主要设计用于与 TabooLib 的配置系统一起使用，不建议单独使用
> 在 YamlCommentLoader 中被用于处理带有注释的 YAML 文件