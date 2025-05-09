# ConfigFile
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConfigFile
- 基本用途: 表示一个配置文件，提供配置文件的读写、加载、保存和重载功能
- 类型: 类 (Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> file: File? -> 与此配置关联的文件对象，可为 null
> name: String -> 配置文件的名称（不包含扩展名）
> reloadCallback: ArrayList<Runnable> -> 存储重载回调的列表（私有）

### 类方法
> onReload(runnable: Runnable) -> 添加一个在配置重载时执行的回调
> saveToString(): String -> 将配置保存为字符串
> saveToFile(file: File? = null) -> 将配置保存到指定文件
> loadFromFile(file: File) -> 从指定文件加载配置
> loadFromString(contents: String) -> 从字符串加载配置
> loadFromReader(reader: Reader) -> 从 Reader 加载配置
> loadFromInputStream(inputStream: InputStream) -> 从 InputStream 加载配置
> reload() -> 重新加载配置
> changeType(type: Type) -> 更改配置的类型
> parser(): ConfigParser<out Config> -> 获取与当前配置格式相关联的解析器（私有）

## 实现细节
- 继承自 ConfigSection 类并实现 Configuration 接口
- 使用 NightConfig 库作为底层配置实现
- 在加载配置文件失败时会自动创建带时间戳的备份文件（.bak）
- 支持从多种来源加载配置：文件、字符串、Reader、InputStream
- 提供配置重载回调机制，允许在配置重载时执行自定义操作
- 支持更改配置类型，会递归处理所有嵌套的配置节点

## 使用场景
> 作为插件配置文件的基础实现类
> 需要从文件、字符串或流加载配置数据
> 需要在配置重载时执行特定操作
> 需要在运行时更改配置类型

## 注意事项
> 使用 saveToFile 方法时，如果未指定文件且当前未关联文件，将抛出异常
> 加载配置文件失败时会自动创建备份，并抛出原始异常
> reload 方法依赖于已设置的 file 属性，如果 file 为 null 则不执行任何操作
> changeType 方法会递归处理所有嵌套的配置节点，对于大型配置可能会有性能影响

