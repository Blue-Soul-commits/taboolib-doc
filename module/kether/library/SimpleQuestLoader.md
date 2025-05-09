# SimpleQuest

## 基本信息
- 类名和包路径: taboolib.library.kether.SimpleQuest
- 基本用途: 实现 Quest 接口，表示一个已解析的 Kether 脚本，包含多个代码块和它们的动作
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> content: char[] -> 存储原始脚本内容的字符数组
> id: String -> 脚本的唯一标识符
> map: Map<String, Block> -> 存储脚本中所有代码块的映射表，以块名为键

### 类方法
> SimpleQuest(content: char[], map: Map<String, Block>, id: String) -> 构造函数，创建包含指定内容、块映射和ID的脚本对象
> getContent(): char[] -> 获取脚本的原始内容
> getId(): String -> 获取脚本的标识符
> getBlock(label: String): Optional<Block> -> 通过名称获取指定的代码块
> getBlocks(): Map<String, Block> -> 获取所有代码块的不可修改映射
> blockOf(action: ParsedAction<?>): Optional<Block> -> 查找包含指定动作的代码块
> toString(): String -> 返回脚本的字符串表示

## 内部类 SimpleBlock
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> label: String -> 代码块的名称标签
> actions: List<ParsedAction<?>> -> 存储代码块中所有动作的列表

### 类方法
> SimpleBlock(label: String, actions: List<ParsedAction<?>>) -> 构造函数，创建指定名称和动作列表的代码块
> getLabel(): String -> 获取代码块的名称
> getActions(): List<ParsedAction<?>> -> 获取代码块中的所有动作
> indexOf(action: ParsedAction<?>): int -> 获取指定动作在列表中的索引位置
> get(i: int): Optional<ParsedAction<?>> -> 获取指定索引位置的动作
> toString(): String -> 返回代码块的字符串表示

## 实现细节
- 实现 Quest 接口，提供对 Kether 脚本结构的表示
- 使用块映射（map）存储脚本中所有命名代码块
- 通过 ActionProperties.BLOCK 属性找到动作对应的代码块
- 提供不可修改的块映射访问，防止外部修改内部状态
- SimpleBlock 类实现了 Quest.Block 接口，表示具体的代码块结构

## 使用场景
> 由 BlockReader 解析脚本源代码后创建，表示完整的脚本结构
> 在 QuestContext 上下文中执行，提供代码块和动作的访问
> 在 SimpleQuestLoader 中作为解析结果返回
> 在脚本执行引擎中用于定位代码块和跟踪动作执行

## 注意事项
> content 字段存储原始脚本内容，用于错误报告和调试
> 代码块标识（label）必须唯一，通常遵循 "main" 或其他命名规则
> 动作通过 ActionProperties.BLOCK 属性与其所属代码块关联
> 修改 SimpleQuest 实例的内部状态可能导致执行时错误
