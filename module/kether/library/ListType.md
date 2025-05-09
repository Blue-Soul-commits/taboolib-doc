# ListType

## 基本信息
- 类名和包路径: taboolib.library.kether.ListType
- 基本用途: 实现 ArgType 接口，用于解析和转换方括号包围的列表结构
- 类型: 泛型类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> elementType: ArgType<T> -> 列表元素的类型转换器

### 类方法
> ListType(elementType: ArgType<T>) -> 构造函数，接收列表元素的类型转换器
> read(reader: QuestReader): List<T> -> 从 QuestReader 读取格式为 [元素1 元素2 ...] 的列表

## 实现细节
- ListType 实现了 ArgType<List<T>> 接口，专门用于解析列表结构
- 构造函数访问级别为包级私有（package-private），主要通过 ArgTypes.listOf 方法创建实例
- read 方法的实现步骤：
  1. 验证起始字符 "["
  2. 循环读取所有元素，直到遇到结束字符 "]"
  3. 使用提供的 elementType 转换器解析每个元素
  4. 确保列表以 "]" 结束
  5. 返回解析完成的列表

## 使用场景
> 在 Kether 脚本中解析列表结构，如 [1, 2, 3] 或 [action1 action2 action3]
> 通过 ArgTypes.listOf 方法与其他类型转换器结合使用
> 用于解析各种类型的列表，包括动作列表、数值列表等

## 注意事项
> ListType 不直接实例化，应使用 ArgTypes.listOf 方法创建
> 列表元素之间不需要分隔符（如逗号），空格分隔即可
> 列表必须用方括号 "[" 和 "]" 包围
