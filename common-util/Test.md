# Test

## 基本信息
- 类名和包路径: taboolib.common.Test
- 基本用途: 提供测试框架基础结构
- 类型: Kotlin抽象类
- 所属模块: common

## 类结构
### 公开抽象方法
> check(): List<Result> -> 运行测试并返回结果列表

### 嵌套类
> sealed class Result(val reason: String) -> 测试结果基类
> class Success(reason: String): Result -> 成功结果
> class Failure(reason: String, val error: Throwable): Result -> 失败结果
> class Unsupported(reason: String): Result -> 不支持的测试结果
> data class BatchResult(val results: List<Result>) -> 批量测试结果

### 伴生对象方法
> check(vararg tests: Test): BatchResult -> 批量执行测试
> sandbox(reason: String, func: Runnable): Result -> 在安全环境中运行测试

## 实现细节
- 使用密封类(sealed class)表示测试结果，确保类型安全
- 每种结果类型都有工厂方法，简化创建过程
- `check()`方法使用`runCatching`捕获异常，确保一个测试失败不会影响其他测试
- `sandbox()`方法特殊处理`UnsupportedVersionException`，将其标记为不支持而非失败
- `BatchResult`提供结果统计和格式化输出功能

## 使用场景
> 创建自动化测试套件
> 验证功能在不同环境下的兼容性
> 检测插件与服务器版本的兼容性
> 生成测试报告

## 注意事项
> 测试应该是独立的，一个测试的失败不应影响其他测试
> 详细模式下会打印完整堆栈跟踪，可能输出较多
> 测试结果格式化输出依赖于PrimitiveIO
