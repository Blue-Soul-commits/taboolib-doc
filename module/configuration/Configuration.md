# Configuration
## 基本信息
- 类名和包路径: taboolib.module.configuration.Configuration
- 基本用途: 提供配置文件的读写、加载、保存和序列化/反序列化功能的接口
- 类型: 接口 (Interface)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> parse(any: Any, type: Type = Type.YAML, concurrent: Boolean = true): ConfigurationSection -> 识别并解析可能的配置部分类型
> empty(type: Type = Type.YAML, concurrent: Boolean = true): Configuration -> 创建空配置
> loadFromFile(file: File, type: Type? = null, concurrent: Boolean = true): Configuration -> 从文件加载配置
> loadFromReader(reader: Reader, type: Type = Type.YAML, concurrent: Boolean = true): Configuration -> 从Reader加载配置
> loadFromString(contents: String, type: Type = Type.YAML, concurrent: Boolean = true): Configuration -> 从字符串加载配置
> loadFromInputStream(inputStream: InputStream, type: Type = Type.YAML, concurrent: Boolean = true): Configuration -> 从输入流加载配置
> loadFromOther(otherConfig: Any, type: Type = Type.YAML, concurrent: Boolean = true): Configuration -> 从其他配置对象加载
> ConfigurationSection.toObject<T>(ignoreConstructor: Boolean = false): T -> 将配置部分反序列化为对象
> ConfigurationSection.getObject<T>(key: String, ignoreConstructor: Boolean = false): T -> 获取配置值并反序列化为对象
> ConfigurationSection.getObject<T>(key: String, obj: T, ignoreConstructor: Boolean = false): T -> 获取配置值并反序列化到现有对象
> ConfigurationSection.setObject(key: String, obj: Any) -> 序列化对象并写入配置
> serialize(obj: Any, type: Type = Type.YAML, concurrent: Boolean = true): ConfigurationSection -> 将对象序列化为配置部分
> deserialize<T>(section: ConfigurationSection, ignoreConstructor: Boolean = false): T -> 将配置部分反序列化为对象
> deserialize<T>(section: ConfigurationSection, obj: T, ignoreConstructor: Boolean = false): T -> 将配置部分反序列化到现有对象
> fromMap(map: Map<*, *>, type: Type = Type.YAML, concurrent: Boolean = true): ConfigurationSection -> 从Map创建配置部分
> getTypeFromFile(file: File, def: Type = Type.YAML): Type -> 根据文件确定配置类型
> getTypeFromExtension(extension: String, def: Type = Type.YAML): Type -> 根据文件扩展名确定配置类型
> getTypeFromExtensionOrNull(extension: String): Type? -> 根据文件扩展名确定配置类型，可能返回null

### 类内可被访问字段
> file: File? -> 与配置关联的文件对象

### 类方法
> saveToString(): String -> 将配置保存为字符串
> saveToFile(file: File? = null) -> 将配置保存到文件
> loadFromFile(file: File) -> 从文件加载配置
> loadFromString(contents: String) -> 从字符串加载配置
> loadFromReader(reader: Reader) -> 从Reader加载配置
> loadFromInputStream(inputStream: InputStream) -> 从输入流加载配置
> reload() -> 重新加载配置
> onReload(runnable: Runnable) -> 注册配置重载时的回调函数
> changeType(type: Type) -> 更改配置类型

## 实现细节
- 继承自 ConfigurationSection 接口，提供了配置节点的基本操作
- 支持多种配置格式：YAML、TOML、JSON、HOCON
- 提供了并发安全的配置实现选项
- 使用 NightConfig 库作为底层配置实现
- 支持对象与配置之间的序列化和反序列化
- 可以根据文件扩展名自动识别配置类型

## 使用场景
> 加载和保存插件配置文件
> 在运行时修改和保存配置
> 将配置数据序列化/反序列化为对象
> 支持多种格式的配置文件处理
> 实现配置文件的自动重载功能

## 注意事项
> 使用 concurrent=true 参数可以获得线程安全的配置实现
> 反序列化时可以选择是否忽略构造函数（ignoreConstructor 参数）
> 配置类型会根据文件扩展名自动识别，也可以手动指定
> 序列化和反序列化功能依赖于 NightConfig 的 ObjectConverter

