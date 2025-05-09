# String.parseUUID
## 基本信息
- 类名和包路径: taboolib.common5.util.String.parseUUID (Kotlin 扩展函数)
- 基本用途: 将字符串安全地解析为 UUID 对象
- 类型: 扩展函数
- 所属模块: common5-legacy-api

## 类结构
### 公开静态方法
> String.parseUUID(): UUID? -> 尝试将字符串解析为 UUID 对象，失败时返回 null

## 实现细节
- 使用 Kotlin 的 runCatching 函数包装 UUID.fromString 调用，确保异常安全
- 通过 getOrNull() 在解析失败时返回 null，而不是抛出异常
- 内部使用 Java 标准库的 UUID.fromString 方法进行实际解析

## 使用场景
> 解析可能格式不正确的 UUID 字符串
> 处理用户输入的 UUID
> 从配置文件或数据库中读取 UUID 字符串

## 注意事项
> 当输入字符串不符合 UUID 格式时，函数返回 null 而不是抛出异常
> 标准 UUID 格式为：xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx (8-4-4-4-12 格式的十六进制数)

