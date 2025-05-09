# BlockReader

## 基本信息
- 类名和包路径: taboolib.library.kether.BlockReader
- 基本用途: 负责解析 Kether 脚本文本，将其转换为结构化的 Quest 对象
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> blocks: Map<String, Quest.Block> -> 存储解析出的代码块集合
> service: QuestService<?> -> 关联的脚本服务实例
> namespace: List<String> -> 命名空间列表，用于解析动作时查找
> currentBlock: String -> 当前正在解析的代码块名称

### 类方法
> BlockReader(content: char[], service: QuestService<?>, namespace: List<String>) -> 使用指定字符内容、服务和命名空间创建解析器
> BlockReader(arr: char[], index: int, mark: int, blocks: Map<String, Quest.Block>, service: QuestService<?>, namespace: List<String>, currentBlock: String) -> 完整参数构造方法
> parse(id: String): Quest -> 解析整个脚本内容，并返回关联到指定 id 的 Quest 对象
> readBlock(): void -> 读取并解析一个代码块定义
> checkLiteral(actions: List<ParsedAction<?>>) -> 检查动作列表中的字面量是否合法
> readActions(): List<ParsedAction<?>> -> 读取一组动作定义
> readAnonymousAction(): ParsedAction<?> -> 读取并处理一个匿名动作块
> newActionReader(service: QuestService<?>, namespace: List<String>): SimpleReader -> 创建用于解析动作的 SimpleReader
> nextAnonymousBlockName(): String -> 生成下一个匿名块的名称
> processActions(block: Quest.Block, actions: List<ParsedAction<?>>): void -> 处理解析出的动作列表
> lineOf(chars: char[], index: int): int -> 计算指定索引位置在源码中的行号
> getBlocks(): Map<String, Quest.Block> -> 获取解析出的所有代码块
> getService(): QuestService<?> -> 获取服务实例
> getNamespace(): List<String> -> 获取命名空间列表
> getCurrentBlock(): String -> 获取当前正在解析的代码块名称

## 实现细节
- 继承自 AbstractStringReader，具备基础的字符串解析能力
- 实现了 Kether 脚本的块结构解析，将源代码解析为结构化的代码块和动作
- 支持匿名块处理，能够动态生成块名称并正确维护块间引用关系
- 对于解析错误，提供了详细的错误位置和上下文信息
- 使用 SimpleQuest 和 SimpleQuest.SimpleBlock 来构建解析结果

## 使用场景
> 作为 QuestLoader 实现的核心组件，用于从文本内容加载 Kether 脚本
> 被 SimpleQuestLoader 和其子类如 KetherScriptLoader 使用
> 在 Kether 脚本引擎中用于解析和加载脚本文件

## 注意事项
> 块定义必须遵循特定语法，以 "def blockName = {}" 形式定义
> 解析过程中出现错误会抛出 LocalizedException 异常，包含详细的错误信息
> 在使用自定义解析器时，可以通过继承并重写 newActionReader 方法来扩展功能
