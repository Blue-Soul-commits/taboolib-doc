# DefaultRegistry

## 基本信息
- 类名和包路径: taboolib.library.kether.DefaultRegistry
- 基本用途: 实现 QuestRegistry 接口，管理 Kether 脚本引擎中的动作解析器和字符串处理器
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> parsers: Map<String, Map<String, QuestActionParser>> -> 存储不同命名空间下的动作解析器映射
> processors: Map<String, BiFunction<QuestContext.Frame, String, String>> -> 存储字符串处理器映射

### 类方法
> registerAction(namespace: String, id: String, parser: QuestActionParser): void -> 在指定命名空间注册动作解析器
> registerAction(id: String, parser: QuestActionParser): void -> 在默认命名空间 "kether" 注册动作解析器
> registerStringProcessor(id: String, processor: BiFunction<QuestContext.Frame, String, String>): void -> 注册字符串处理器
> unregisterAction(id: String): void -> 从默认命名空间移除动作解析器
> unregisterAction(namespace: String, id: String): void -> 从指定命名空间移除动作解析器，如果 id 为 "*" 则清空整个命名空间
> getRegisteredActions(namespace: String): Collection<String> -> 获取指定命名空间中已注册的所有动作 ID
> getRegisteredActions(): Collection<String> -> 获取默认命名空间中已注册的所有动作 ID
> getRegisteredNamespace(): Collection<String> -> 获取所有已注册的命名空间
> getParser(id: String, namespace: String): Optional<QuestActionParser> -> 获取特定命名空间中的动作解析器
> getParser(id: String, namespace: List<String>): Optional<QuestActionParser> -> 按照优先级在多个命名空间中查找动作解析器
> getParser(id: String): Optional<QuestActionParser> -> 在默认命名空间中查找动作解析器
> getStringProcessor(id: String): Optional<BiFunction<QuestContext.Frame, String, String>> -> 获取指定 ID 的字符串处理器

## 实现细节
- 使用嵌套 Map 数据结构存储动作解析器，外层 Map 以命名空间为键，内层 Map 以动作 ID 为键
- 支持命名空间管理，允许不同插件或模块注册同名但不同功能的动作
- 支持通过 "命名空间:动作ID" 格式来查找特定命名空间下的动作
- 当查找动作解析器时，会按照提供的命名空间列表顺序依次查找，直到找到第一个匹配项
- 提供对字符串处理器的支持，这些处理器可用于在脚本执行期间转换字符串内容

## 使用场景
> 作为 QuestService 的组件，为 Kether 脚本引擎提供动作注册和查找功能
> 在自定义 Kether 动作开发中，将动作解析器注册到特定命名空间
> 提供字符串处理功能，用于在脚本中执行字符串转换操作
> 在 Kether 脚本引擎初始化过程中设置基础动作和处理器

## 注意事项
> 默认命名空间为 "kether"，与无命名空间的方法调用直接关联
> 使用 "*" 作为 ID 进行注销操作时会清空整个命名空间的所有动作
> 动作解析器和字符串处理器之间没有直接关联，它们是独立的功能组件
