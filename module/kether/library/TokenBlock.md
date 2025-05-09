# TokenBlock

## 基本信息
- 类名和包路径: taboolib.library.kether.TokenBlock
- 基本用途: 表示 Kether 脚本解析过程中的标记块，包含标记内容和类型信息
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> token: String -> 存储标记的实际文本内容
> isBlock: boolean -> 标记该标记是否为块（引号包围的字符串）

### 类方法
> TokenBlock(token: String, isBlock: boolean) -> 构造函数，创建包含指定文本和块标志的标记块
> getToken(): String -> 获取标记文本内容
> isBlock(): boolean -> 检查标记是否为块（引号包围的字符串）

## 实现细节
- 用于在 SimpleReader.nextTokenBlock() 中表示解析出的标记
- isBlock 字段用于区分普通标记和引号（单引号或双引号）包围的字符串
- 对于普通标记（如标识符、数字等），isBlock 为 false
- 对于引号包围的字符串文本，isBlock 为 true

## 使用场景
> 在 SimpleReader 中用于解析脚本标记，保留更多语义信息
> 在 KetherScriptLoader.Reader 中被扩展以提供自定义的标记处理
> 作为文本块和普通标记的区分依据，影响后续解析逻辑
> 在复杂的解析器中，可用于特殊处理字符串类型的参数

## 注意事项
> isBlock 为 true 表示标记是引号包围的块，而不是表示它是代码块
> token 字段存储的是已经去除引号的内容
> 该类主要用于内部解析过程，通常不需要直接在用户代码中创建
