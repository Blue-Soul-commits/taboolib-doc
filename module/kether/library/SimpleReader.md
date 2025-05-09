# SimpleReader

## 基本信息
- 类名和包路径: taboolib.library.kether.SimpleReader
- 基本用途: 实现 QuestReader 接口，提供 Kether 脚本词法和动作解析功能
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> namespace: List<String> -> 存储命名空间列表，用于查找动作解析器
> service: QuestService<?> -> 脚本服务实例，提供对注册表的访问
> blockParser: BlockReader -> 关联的块解析器实例，用于处理匿名块

### 类方法
> SimpleReader(service: QuestService<?>, reader: BlockReader, namespace: List<String>) -> 构造函数，初始化解析器
> nextToken(): String -> 获取下一个标记字符串，覆盖 AbstractStringReader 的实现
> nextTokenBlock(): TokenBlock -> 获取下一个带额外信息的标记块对象
> nextAnonAction(): ParsedAction<?> -> 解析匿名动作块并设置 REQUIRE_FRAME 属性
> nextAction(): ParsedAction<T> -> 获取下一个解析的动作
> nextAction(namespace: String): ParsedAction<T> -> 在指定命名空间下获取下一个解析的动作
> beforeParse(): void -> 动作解析前的钩子方法（空实现，可由子类覆盖）
> wrap(action: QuestAction<T>): ParsedAction<T> -> 将动作包装为 ParsedAction 对象
> expect(value: String): void -> 期望下一个标记为指定值，否则抛出异常
> getNamespace(): List<String> -> 获取命名空间列表
> getService(): QuestService<?> -> 获取脚本服务实例
> getBlockParser(): BlockReader -> 获取块解析器实例

## 实现细节
- 扩展 AbstractStringReader 并实现 QuestReader 接口，继承基础的字符串解析能力
- 实现复杂的字符串标记解析，支持双引号（""）和单引号（''）包围的字符串
- 提供匿名动作块的解析，与 BlockReader 协作处理花括号包围的嵌套动作
- 支持特殊前缀动作解析：花括号（{）表示匿名块、与号（&）表示变量引用、星号（*）表示字面量
- 动作解析逻辑根据命名空间优先级在注册表中查找对应的解析器
- 对于未知动作，当启用宽容解析器模式时会将其视为字面量动作

## 使用场景
> 在 BlockReader 中用于解析脚本动作序列
> 作为 QuestReader 的实现，为 ArgType 类型提供读取能力
> 在扩展的解析器如 KetherScriptLoader.Reader 中被继承和定制
> 在远程脚本执行中被 RemoteQuestReader 映射和代理

## 注意事项
> 默认会将 "kether" 添加到命名空间列表中，作为基础命名空间
> 动作解析依赖于 QuestService 的注册表，确保必要的动作解析器已注册
> 对于未找到解析器的动作标记，取决于 Kether.isAllowToleranceParser 的设置
> 通过 TokenBlock 返回解析的标记，它携带了额外的标志表示是否为块内容
