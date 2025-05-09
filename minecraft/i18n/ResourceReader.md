# ResourceReader
## 基本信息
- 类名和包路径: taboolib.module.lang.ResourceReader
- 基本用途: 负责加载、管理和迁移TabooLib国际化系统的语言资源文件
- 类型: 类
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> files: HashMap<String, LanguageFile> -> 存储语言代码到语言文件的映射
> dateFormat: SimpleDateFormat -> 日期格式化工具，用于记录文件更新时间
> clazz: Class<*> -> 类引用，用于资源定位
> migrate: Boolean -> 是否启用文件迁移功能，默认为true

### 类方法
> loadNodes(file: Configuration, nodesMap: HashMap<String, Type>, code: String): Unit -> 从配置文件中加载语言节点
> loadNode(map: Map<String, Any>, code: String, node: String?): Type? -> 从映射中加载单个语言节点
> migrateFile(missing: List<String>, source: Configuration, file: File): Unit -> 将缺失的键值对迁移到目标文件

## 实现细节
- ResourceReader在初始化时会自动加载和处理语言资源文件
- 遍历Language.languageCode中的所有语言代码，查找并加载对应的语言文件
- 首先从JAR包中读取原始语言文件，然后释放到磁盘上
- 支持文件监听功能，当语言文件发生变化时自动重新加载
- 实现了语言文件的自动迁移功能，当发现缺失的键时会自动添加到文件末尾
- 支持多种类型的语言节点：列表、嵌套配置和普通文本
- 根据配置中的"type"或"=="字段确定节点类型，并实例化相应的Type实现类
- 迁移文件时会添加时间戳注释，便于追踪更新历史

## 使用场景
> 在插件初始化时加载多语言资源文件
> 自动检测和迁移缺失的语言条目，确保语言文件完整性
> 监听语言文件变化，支持热重载功能
> 作为TabooLib国际化系统的核心组件，提供语言资源管理
> 支持多种格式的语言节点，满足不同的消息发送需求

## 注意事项
> 类使用了@Suppress("DEPRECATION")注解，可能包含已弃用的API
> 语言文件必须放在特定路径下(Language.path/语言代码.*)才能被正确识别
> 语言节点必须包含"type"或"=="字段指定类型，否则会输出警告
> 文件监听功能受Language.enableFileWatcher控制，可以禁用以提高性能
> 迁移功能受构造函数中migrate参数控制，可以禁用以防止自动修改文件

## 使用实例
> 基本使用
```kotlin
// 创建ResourceReader实例，自动加载语言文件
val resourceReader = ResourceReader(MyPlugin::class.java)

// 获取特定语言代码的语言文件
val chineseFile = resourceReader.files["zh_CN"]
val englishFile = resourceReader.files["en_US"]

// 手动加载配置文件中的节点
val config = Configuration.loadFromFile(File("custom_lang.yml"))
val nodes = HashMap<String, Type>()
resourceReader.loadNodes(config, nodes, "custom")

// 禁用迁移功能的ResourceReader
val noMigrateReader = ResourceReader(MyPlugin::class.java, migrate = false)

// 语言文件结构示例
/*
welcome:
  type: text
  text: "欢迎 %player% 加入服务器！"

commands:
  - type: text
    text: "/help - 显示帮助信息"
  - type: text
    text: "/stats - 显示统计信息"

notification:
  type: json
  text:
  - "点击 [这里] 查看详情"
  args:
  - hover: "点击查看"
    command: "/details"
*/
```