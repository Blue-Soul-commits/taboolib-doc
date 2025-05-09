# ScriptOptions

## 基本信息
- 类名和包路径: taboolib.module.kether.ScriptOptions
- 基本用途: Kether脚本执行选项的配置类，提供流式API设置脚本执行的各种参数
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> builder(): ScriptOptionsBuilder -> 创建ScriptOptionsBuilder实例，用于构建ScriptOptions
> new(const: ScriptOptionsBuilder.() -> Unit): ScriptOptions -> 使用配置函数构建ScriptOptions实例

### 类内可被访问字段
> useCache: Boolean -> 是否使用脚本缓存，默认为true
> namespace: List<String> -> 脚本解析使用的命名空间列表，默认为空列表
> cache: KetherShell.Cache -> 脚本缓存容器，默认使用KetherShell.mainCache
> sender: ProxyCommandSender? -> 脚本执行者，默认为null
> sandbox: Boolean -> 是否在沙盒模式下执行脚本，默认为false
> detailError: Boolean -> 是否显示详细错误信息，默认为false
> context: ScriptContext.() -> Unit -> 脚本上下文配置函数，默认为空函数
> vars: KetherShell.VariableMap -> 脚本变量容器，存储脚本执行时的初始变量

### 类方法
> 无（主类中没有方法，内部类ScriptOptionsBuilder包含多个方法）

## 实现细节
- ScriptOptions类使用了构建器模式，通过ScriptOptionsBuilder提供流式API
- 所有配置选项都有默认值，可以只设置需要的选项
- 内部类ScriptOptionsBuilder提供了设置各个选项的方法，每个方法都返回this以支持链式调用
- sender方法支持接收任意类型的执行者，内部会自动适配为ProxyCommandSender
- vars方法提供了多种重载，支持不同形式的变量设置
- 使用静态方法builder()和new()简化构建器的创建和使用

## 使用场景
> 配置Kether脚本的执行环境和参数
> 设置脚本执行者和初始变量
> 控制脚本缓存行为，提高性能
> 配置安全执行模式和错误处理策略

## 注意事项
> 默认使用全局缓存(KetherShell.mainCache)，多个脚本共享可能导致冲突
> sandbox=true时脚本执行不会抛出异常，而是捕获并处理错误
> detailError选项只在sandbox=true时有效
> 变量容器vars使用的是KetherShell.VariableMap，支持多种形式的变量设置
