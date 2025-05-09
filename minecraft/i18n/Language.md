# Language
## 基本信息
- 类名和包路径: taboolib.module.lang.Language
- 基本用途: TabooLib国际化系统的核心类，管理语言文件、文本转换和本地化功能
- 类型: 单例对象(object)
- 所属模块: minecraft-i18n

## 类结构
### 公开静态字段
> path: String -> 语言文件路径，默认为"lang"
> releasePath: String -> 语言文件释放路径，默认为"plugins/{0}/lang/{1}"
> default: String -> 默认语言文件，默认为"zh_CN"
> textTransfer: ArrayList<TextTransfer> -> 文本转换器列表
> languageFile: HashMap<String, LanguageFile> -> 语言文件缓存，键为语言代码，值为LanguageFile对象
> languageCode: HashSet<String> -> 语言文件代码集合
> languageCodeTransfer: HashMap<String, String> -> 语言文件代码转换映射
> languageType: HashMap<String, Class<out Type>> -> 语言文件类型映射，键为类型名称，值为Type实现类
> enableSimpleComponent: Boolean -> 是否在语言文件中启用SimpleComponent格式化，默认为false
> enableFileWatcher: Boolean -> 是否启用文件监听，默认为false

### 公开静态方法
> setRoot(path: String): Unit -> 重设根目录，影响语言文件释放路径
> addLanguage(vararg code: String): Unit -> 添加新的语言文件代码
> getLocale(player: ProxyPlayer): String -> 获取玩家的语言设置
> getLocale(): String -> 获取控制台的语言设置
> reload(): Unit -> 重新加载语言文件

### 类内可被访问字段
> isFirstLoaded: Boolean -> 是否完成了首次加载，私有字段

### 类方法
> call(name: String, data: Array<out Any>?): OpenResult -> 实现OpenListener接口的方法，处理外部调用

## 实现细节
- Language是一个单例对象，使用@Awake和@Inject注解标记为TabooLib的自动加载组件
- 实现了OpenListener接口，支持通过TabooLib的开放API进行调用
- 在初始化时(LifeCycle.INIT)自动调用reload方法加载语言文件
- 首次加载时会扫描JAR包中的语言文件，自动识别语言代码
- 支持语言代码转换，如将"zh_hans_cn"转换为"zh_CN"
- 提供了多种语言文件类型的支持，如文本、JSON、标题、声音等
- 通过PlayerSelectLocaleEvent和SystemSelectLocaleEvent事件允许修改语言选择
- 支持文件监听功能，可以在语言文件变化时自动重新加载
- 通过OpenResult接口提供了三个外部调用点：重载语言文件、获取语言代码和获取语言文件列表

## 使用场景
> 作为TabooLib国际化系统的核心组件，管理多语言资源
> 在插件初始化时自动加载语言文件，支持多种格式和类型
> 根据玩家客户端设置或服务器设置提供适当的语言版本
> 通过textTransfer系统支持文本转换，如颜色代码处理
> 提供统一的语言文件类型注册和管理机制

## 注意事项
> 语言文件路径默认为"lang"，可以通过修改path字段更改
> 语言文件释放路径默认为"plugins/{0}/lang/{1}"，其中{0}为插件ID，{1}为文件名
> 默认语言为"zh_CN"(简体中文)，可以通过修改default字段更改
> 文件监听功能(enableFileWatcher)从2024/11/20起默认禁用，需要手动启用
> SimpleComponent格式化(enableSimpleComponent)默认禁用，需要手动启用
> 添加新的语言代码后，如果已经完成首次加载，会自动重新加载语言文件

