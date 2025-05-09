# Quest

## 基本信息
- 类名和包路径: taboolib.library.kether.Quest
- 基本用途: 表示 Kether 脚本中的一个完整的脚本单元，包含多个执行块
- 类型: 接口
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> getId(): String -> 获取脚本的唯一标识符
> getBlock(label: String): Optional<Block> -> 根据标签获取特定的脚本块
> getBlocks(): Map<String, Block> -> 获取脚本中所有的块
> blockOf(action: ParsedAction<?>): Optional<Block> -> 查找包含特定动作的块

### 嵌套接口 Block
> getLabel(): String -> 获取块的标签
> getActions(): List<ParsedAction<?>> -> 获取块中的所有动作
> indexOf(action: ParsedAction<?>): int -> 查找特定动作在块中的索引位置
> get(i: int): Optional<ParsedAction<?>> -> 获取块中指定索引位置的动作

## 实现细节
- Quest 接口定义了 Kether 脚本的基本结构
- 每个 Quest 由多个命名的 Block 组成，每个 Block 包含一系列动作
- 主要实现类是 SimpleQuest，它在内部使用 Map 存储所有的 Block
- 脚本中动作通过 ActionProperties.BLOCK 属性与它所属的 Block 关联
- Block 接口定义在 Quest 内部，表示脚本的一个代码块

## 使用场景
> 表示已解析的 Kether 脚本结构
> 通过 QuestLoader 加载脚本文件来创建
> 在 QuestContext 中执行脚本
> 管理脚本中的不同代码块和动作序列

## 注意事项
> 脚本中必须至少有一个名为 "main" 的块，作为入口点
> 可以有一个特殊的 "settings" 块，用于存储脚本设置
> 脚本块之间可以相互调用，形成复杂的控制流
> 在执行时，可以通过 QuestContext.Frame 访问和操作脚本块

