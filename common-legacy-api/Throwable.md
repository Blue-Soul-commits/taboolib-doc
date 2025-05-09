# Throwable 堆栈跟踪工具
## 基本信息
- 类名和包路径: taboolib.common5.util (Kotlin 扩展函数)
- 基本用途: 提供异常堆栈跟踪的字符串转换工具
- 类型: 扩展函数
- 所属模块: common5-legacy-api

## 类结构
### 公开静态方法
> Throwable.getStackTraceString(): String -> 将异常的堆栈跟踪转换为字符串
> Throwable.getStackTraceStringList(): List<String> -> 将异常的堆栈跟踪转换为字符串列表

## 实现细节
- 两个函数都使用 StringWriter 和 PrintWriter 捕获异常的堆栈跟踪信息
- getStackTraceString 返回完整的堆栈跟踪作为单个字符串
- getStackTraceStringList 将堆栈跟踪分割为行列表，使用 Kotlin 的 lines() 函数
- 这些函数提供了比 Java 内置 printStackTrace() 更灵活的堆栈跟踪处理方式

## 使用场景
> 记录异常信息到日志文件
> 在用户界面中显示错误详情
> 发送错误报告到远程服务器
> 调试和错误分析
> 自定义错误处理和格式化

## 注意事项
> 堆栈跟踪可能包含敏感信息，在向用户展示或发送到外部服务前应考虑安全性
> 完整的堆栈跟踪可能很长，在用户界面显示时应考虑适当截断
> 这些函数在内存使用上比直接使用 printStackTrace() 更重，因为它们创建了字符串副本
