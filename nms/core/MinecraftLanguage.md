# MinecraftLanguage

## 基本信息
- 类名和包路径: taboolib.module.nms.MinecraftLanguage
- 基本用途: 提供 Minecraft 原版语言文件的加载和访问功能
- 类型: 单例对象
- 所属模块: bukkit-nms

## 类结构

### 扩展函数
> Player.getMinecraftLanguageFile(): LanguageFile? -> 获取玩家对应的语言文件

### 内部接口和类
> LanguageFile -> 语言文件接口
  - sourceFile: File -> 原始文件
  - container: Any -> 容器对象
  - get(path: String): String? -> 获取语言文件值
  - get(localeKey: LanguageKey): String? -> 获取语言文件值（支持额外信息）
  
> LanguageFile.FormatProperties -> 1.8-1.12 版本语言文件格式（Properties）
> LanguageFile.FormatJson -> 1.13+ 版本语言文件格式（JSON）

> LanguageKey -> 语言文件节点数据类
  - type: Type -> 节点类型（NORMAL, SPECIAL, DEFAULT）
  - path: String -> 节点路径
  - extra: String? -> 额外信息（低版本中表现为生成蛋的类型）

### 公开字段
> resourceUrl: String -> 资源文件地址
> supportedLanguage: ArrayList<String> -> 支持的语言文件列表
> files: HashMap<String, LanguageFile> -> 已加载的语言文件

### 公开方法
> getLanguageFile(locale: String): LanguageFile? -> 获取指定语言的语言文件
> getDefaultLanguageFile(): LanguageFile? -> 获取默认语言文件（zh_cn）

### 私有方法
> init() -> 初始化语言文件
> loadFilesFromExchange(): Boolean -> 从 Exchanges 空间中获取语言文件
> saveExchanges() -> 将已加载的语言文件写入到 Exchange 空间
> checkFiles(): Boolean -> 检查语言文件是否完整
> downloadFiles() -> 下载语言文件
> loadFiles() -> 加载语言文件
> readJson(url: String): JsonObject -> 读取 JSON 数据
> getFile(locale: String): File -> 获取语言文件路径
> getFiles(): Map<String, File> -> 获取所有可用的语言文件

## 实现细节
- 使用 @Inject 和 @PlatformSide 注解标记为 Bukkit 平台的注入对象
- 支持从 Minecraft 官方资源服务器下载语言文件
- 根据 Minecraft 版本自动选择适当的语言文件格式（Properties 或 JSON）
- 使用 SHA-1 哈希值作为语言文件的本地存储路径
- 通过 Exchanges 机制在插件间共享语言文件，避免重复加载
- 支持获取玩家客户端语言对应的语言文件

## 使用场景
> 获取 Minecraft 原版物品、实体、附魔等的本地化名称
> 根据玩家客户端语言显示适当的文本
> 实现多语言支持的插件功能
> 获取特定语言的 Minecraft 原版翻译

## 注意事项
> 默认支持的语言包括 zh_cn（简体中文）、zh_tw（繁体中文）和 en_gb（英式英语）
> 当请求 en_us（美式英语）时，会返回 en_gb 作为替代
> 语言文件会在插件初始化时自动下载和加载
> 语言文件存储在 assets 目录下，使用哈希值作为文件名
