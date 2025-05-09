# DigestExtensions

## 基本信息
- 类名和包路径: taboolib.common.io (扩展函数文件)
- 基本用途: 提供计算数字签名(哈希值)的扩展函数
- 类型: Kotlin扩展函数集合
- 所属模块: common-io

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> String.digest(algorithm: String): String -> 计算字符串的数字签名
> ByteArray.digest(algorithm: String): String -> 计算字节数组的数字签名
> File.digest(algorithm: String): String -> 计算文件的数字签名

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- 所有方法默认使用SHA-1算法，但支持指定其他算法
- 字符串计算前会转换为UTF-8编码的字节数组
- 文件计算使用NIO的FileChannel和直接缓冲区，提高大文件处理效率
- 使用Java 8兼容的方式处理ByteBuffer的flip和clear操作

## 使用场景
> 验证文件完整性，如下载后的校验
> 生成内容的唯一标识符，如缓存键
> 安全相关场景，如密码哈希(虽然不推荐直接使用这些函数存储密码)

## 注意事项
> 对于大文件，计算过程可能较慢，应考虑在非主线程中执行
> 不同算法生成的哈希值长度不同，如MD5为32位，SHA-1为40位
> 这些函数返回的是十六进制字符串形式的哈希值
