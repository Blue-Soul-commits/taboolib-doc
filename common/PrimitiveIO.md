# PrimitiveIO  
## 基本信息  
- 类名和包路径: taboolib.common.PrimitiveIO  
- 基本用途: 提供基础的 IO 操作和本地化功能  
- 类型: 工具类  
- 所属模块: Common  
---
## 类结构  
  
### 公开静态字段  
> HEX_ARRAY: char[] -> 用于十六进制转换的字符数组  
> BUFFER_SIZE: int -> 缓冲区大小，默认为 8192  
> runningFileName: String -> 当前运行的文件名  
> isChineseEnvironment: boolean -> 是否为中文环境  
  
### 公开静态方法  
> debug(message: Object, args: Object...): void -> 调试模式输出  
> println(message: Object, args: Object...): void -> 控制台信息输出  
> warning(message: Object, args: Object...): void -> 控制台警告输出  
> error(message: Object, args: Object...): void -> 控制台错误输出  
> validation(file: File, hashFile: File): boolean -> 验证文件完整性  
> getHash(file: File): String -> 获取文件哈希，使用 sha-1 算法  
> getHash(data: String): String -> 获取字符串哈希  
> bytesToHex(bytes: byte[]): String -> 字节数组转十六进制字符串  
> readFile(file: File): String -> 读取文件内容  
> readFully(inputStream: InputStream, charset: Charset): String -> 从输入流读取全部内容  
> readFully(inputStream: InputStream): byte[] -> 从输入流读取全部内容  
> copyFile(from: File, to: File): File -> 通过 FileChannel 复制文件  
> downloadFile(url: URL, out: File): void -> 下载文件  
> getRunningFileName(): String -> 获取当前运行的文件名  
> isChineseEnvironment(): boolean -> 获取当前是否为中文环境  
> t(zh: String, en: String): String -> 返回对应语言环境的本地化文本  
  
### 类内可被访问字段  
> DIGEST_THREAD_LOCAL: ThreadLocal<MessageDigest> -> 线程本地摘要算法  
> logger: Logger -> 日志器  
  
### 类方法  
(无实例方法)  
---
## 实现细节  
- 提供文件操作和哈希计算功能  
- 支持中英文环境下的本地化文本输出  
- 使用 ThreadLocal 优化 MessageDigest 实例创建  
---
## 使用场景  
> 文件操作：读取、复制、下载  
> 哈希计算：验证文件完整性  
> 日志输出：调试、信息、警告、错误  
> 本地化文本：支持中英文环境  
---
## 注意事项  
> 获取语言环境失败时默认视为中文环境  
> 日志输出会使用当前运行的文件名作为前缀  