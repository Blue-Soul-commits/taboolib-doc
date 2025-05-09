# SimpleQuest

## 基本信息
- 类名和包路径: taboolib.library.kether.SimpleQuest
- 基本用途: 实现 Quest 接口，表示一个完整的 Kether 脚本，包含多个代码块
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> content: char[] -> 存储脚本的原始字符内容
> id: String -> 脚本的唯一标识符
> map: Map<String, Block> -> 存储所有代码块的映射，键为代码块名称

### 类方法
> SimpleQuest(content: char[], map: Map<String, Block>, id: String) -> 构造函数，使用字符内容、代码块映射和ID创建脚本
> getContent(): char[] -> 获取脚本的原始字符内容
> getId(): String -> 获取脚本的唯一标识符
> getBlock(label: String): Optional<Block> -> 根据标签名获取代码块
> getBlocks(): Map<String, Block> -> 获取所有代码块的不可修改映射
> blockOf(action: ParsedAction<?>): Optional<Block> -> 查找包含指定动作的代码块
> toString(): String -> 返回脚本的字符串表示

## 实现细节
- 通过 Map 数据结构存储代码块，实现快速查找
- 提供两种方式查找代码块：通过标签名直接查找和通过动作引用查找
- 对于动作查找，优先使用动作的 BLOCK 属性进行查找，如果不存在则遍历所有代码块
- SimpleBlock 内部类实现了 Quest.Block 接口，用于表示单个代码块
- 代码块由标签和动作列表组成，支持通过索引或动作引用查找特定动作

## 使用场景
> 作为 Kether 脚本引擎的核心数据结构，表示已解析的脚本
> 在脚本执行过程中提供代码块查找和访问功能
> 由 BlockReader 解析脚本文本并构建
> 在 QuestContext 中用于执行脚本

## 注意事项
> 脚本实例是不可变的，一旦创建就不能修改其内容和结构
> 返回的代码块映射是不可修改的，防止外部代码修改脚本结构
> 通过 blockOf 方法查找代码块时，如果动作不属于任何代码块，将返回空 Optional
