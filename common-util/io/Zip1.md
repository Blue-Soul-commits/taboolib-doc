# ZipExtensions

## 基本信息
- 类名和包路径: taboolib.common.io (扩展函数文件)
- 基本用途: 提供文件压缩和解压缩的扩展函数
- 类型: Kotlin扩展函数集合
- 所属模块: common-io

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> File.zip(target: File, skipParent: Boolean): Unit -> 将文件或目录压缩为ZIP文件
> File.unzip(target: File): Unit -> 将ZIP文件解压到指定目录
> File.unzip(destDirPath: String): Unit -> 将ZIP文件解压到指定路径
> ZipOutputStream.putFile(file: File, path: String): Unit -> 将文件添加到ZIP输出流

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- `zip()`函数支持两种模式：
  - 普通模式：将整个文件或目录压缩
  - 跳过父目录模式：只压缩目录中的内容，不包含父目录本身
- `unzip()`函数自动创建必要的目录结构
- 所有函数都使用Kotlin的`use`函数确保资源正确关闭
- `putFile()`是递归函数，用于处理目录结构

## 使用场景
> 需要创建插件数据的备份
> 需要打包多个文件为单个文件进行传输
> 需要解压用户上传的ZIP文件
> 需要处理模组或资源包

## 注意事项
> 压缩大文件或目录可能耗时较长，考虑在非主线程中执行
> 解压不安全的ZIP文件可能导致路径遍历漏洞，应验证ZIP内容
> 这些函数不支持加密ZIP文件
