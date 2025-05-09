# Base64 编码/解码扩展函数
## 基本信息
- 类名和包路径: taboolib.common5.util (Kotlin 扩展函数集)
- 基本用途: 提供 ByteArray 和 String 类型的 Base64 编码和解码功能
- 类型: 扩展函数集
- 所属模块: common5-legacy-api

## 类结构
### 公开静态方法
> ByteArray.encodeBase64(): String -> 将字节数组编码为 Base64 字符串
> String.encodeBase64(): String -> 将字符串编码为 Base64 字符串
> ByteArray.decodeBase64(): ByteArray -> 将 Base64 编码的字节数组解码
> String.decodeBase64(): ByteArray -> 将 Base64 编码的字符串解码为字节数组

## 实现细节
- 使用 Java 标准库中的 Base64 类进行编码和解码操作
- 编码时使用 Base64.getEncoder() 获取编码器
- 解码时使用 Base64.getDecoder() 获取解码器
- 字符串与字节数组的转换使用 UTF-8 编码 (StandardCharsets.UTF_8)
- 所有函数都是无状态的，可以安全地在多线程环境中使用

## 使用场景
> 数据传输前的编码，确保二进制数据可以安全传输
> 简单的数据混淆或模糊处理
> 处理需要 Base64 格式的 API 请求和响应
> 图片或其他二进制数据的文本表示

## 注意事项
> ByteArray.encodeBase64() 可能存在实现问题，直接调用 toString() 可能不会产生预期的 Base64 字符串
> 同样，String.encodeBase64() 也可能有相同的问题
> 这些函数不提供 URL 安全的 Base64 变体
> 不包含填充选项控制
