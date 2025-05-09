# FileCreation

## 基本信息
- 类名和包路径: taboolib.common.io (扩展函数文件)
- 基本用途: 提供简化的文件和目录创建函数
- 类型: Kotlin工具函数集合
- 所属模块: common-io

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> newFile(file: File, path: String, create: Boolean, folder: Boolean): File -> 在指定文件夹下创建文件或目录
> newFile(path: String, create: Boolean, folder: Boolean): File -> 根据路径创建文件或目录
> newFile(file: File, create: Boolean, folder: Boolean): File -> 创建指定文件对象表示的文件或目录
> newFolder(folder: File, path: String, create: Boolean): File -> 在指定文件夹下创建目录
> newFolder(path: String, create: Boolean): File -> 根据路径创建目录

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 所有函数都基于核心的`newFile(File, Boolean, Boolean)`实现
- 自动创建父目录，确保文件路径存在
- 根据参数决定是创建文件还是目录
- 支持仅声明而不创建文件的模式

## 使用场景
> 需要确保文件存在时，如配置文件、数据文件等
> 需要创建多级目录结构时
> 需要在特定目录下创建文件或子目录时

## 注意事项
> 默认情况下会创建不存在的文件或目录
> 如果指定`create=false`，则只返回File对象而不创建实际文件
> 这些函数会自动创建父目录，无需手动处理