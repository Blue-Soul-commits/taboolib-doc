# KetherShell

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherShell
- 基本用途: Kether脚本的快速执行工具，提供简便的脚本执行接口和缓存机制
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> mainCache: Cache -> 全局共享的主缓存实例

### 公开静态方法
> eval(source: List<String>, options: ScriptOptions = ScriptOptions()): CompletableFuture<Any?> -> 执行脚本列表，返回异步结果
> eval(source: String, options: ScriptOptions = ScriptOptions()): CompletableFuture<Any?> -> 执行脚本字符串，返回异步结果
> eval(source: List<String>, cacheScript: Boolean, namespace: List<String>, cache: Cache, sender: ProxyCommandSender?, vars: VariableMap?, context: ScriptContext.() -> Unit): CompletableFuture<Any?> -> [已废弃] 执行脚本列表的旧方法
> eval(source: String, cacheScript: Boolean, namespace: List<String>, cache: Cache, sender: ProxyCommandSender?, vars: VariableMap?, context: ScriptContext.() -> Unit): CompletableFuture<Any?> -> [已废弃] 执行脚本字符串的旧方法

### 类内可被访问字段
> 无

### 类方法
> 无

## 实现细节
- KetherShell是一个单例对象，提供简易的脚本执行API
- 主要提供eval方法的多种重载，用于从字符串或字符串列表中执行Kether脚本
- 新版API使用ScriptOptions类封装所有执行选项，提高了可扩展性
- 如果脚本不是以"def "开头，会自动添加"def main = { ... }"包装，简化单行脚本的编写
- 支持脚本缓存机制，通过Cache类存储已解析的脚本以提高性能
- 提供了sandbox模式执行脚本的能力，可以捕获脚本执行过程中的错误
- 包含两个内部类：VariableMap用于临时变量存储，Cache用于脚本缓存

## 使用场景
> 快速执行简短的Kether脚本代码片段
> 在插件功能中集成Kether脚本能力
> 通过缓存机制提高频繁执行的脚本性能
> 在沙盒环境中安全地执行用户提供的脚本

## 注意事项
> 旧版eval方法已被废弃，建议使用新版ScriptOptions-based的API
> 默认使用mainCache全局缓存，多个脚本引擎共享缓存可能导致冲突
> 非def开头的脚本会被自动包装在main代码块中
> 沙盒模式(sandbox=true)可以捕获脚本执行错误，但会消耗更多资源
