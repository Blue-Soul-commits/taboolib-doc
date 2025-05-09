# FileExtensions

## 基本信息
- 类名和包路径: taboolib.common.io (扩展函数文件)
- 基本用途: 提供File类的扩展函数，简化文件操作
- 类型: Kotlin扩展函数集合
- 所属模块: common-io

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> File.notfound(): Boolean -> 检查文件是否不存在
> File.deepCopyTo(target: File): File -> 深度复制文件或目录到目标位置
> File.deep(directionMatcher: (File) -> Boolean): List<File> -> 深度遍历文件或目录

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- `notfound()`: 简单地反转`exists()`方法的结果
- `deepCopyTo()`: 递归复制文件或目录，保持原始结构
- `deep()`: 使用递归方式深度遍历文件系统，支持自定义遍历条件

## 使用场景
> 检查文件不存在的情况，语义更清晰
> 需要复制整个目录结构时，包括所有子目录和文件
> 需要按特定条件遍历文件系统时，如只遍历特定类型的文件

## 注意事项
> `deepCopyTo()`会覆盖目标位置的同名文件
> `deep()`方法在处理大型目录结构时可能导致栈溢出
> 这些扩展函数依赖于Java标准库的File类，继承了其所有限制
