# Workspace

## 基本信息
- 类名和包路径: taboolib.module.kether.Workspace
- 基本用途: Kether脚本工作空间，负责脚本文件的加载、管理和执行
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> file: File -> 工作空间根目录
> extension: String -> 脚本文件扩展名，默认为".ks"
> namespace: List<String> -> 脚本解析使用的命名空间列表，默认为空列表
> scripts: HashMap<String, Script> -> 存储已加载的脚本
> scriptsSetting: HashMap<String, Map<String, Any?>> -> 存储脚本设置
> runningScripts: Multimap<String, ScriptContext> -> 存储正在运行的脚本上下文

### 类方法
> loadAll(): Unit -> 加载所有脚本、设置并启动自动运行的脚本
> loadSettings(): Unit -> 加载所有脚本的设置
> loadScripts(): Unit -> 从文件系统加载脚本文件
> cancelAll(): Unit -> 取消所有正在运行的脚本
> getRunningScript(): List<ScriptContext> -> 获取所有正在运行的脚本上下文
> runScript(id: String, context: ScriptContext): CompletableFuture<Any> -> 运行指定ID的脚本
> terminateScript(context: ScriptContext): Unit -> 终止指定的脚本执行

## 实现细节
- Workspace类管理一个目录下的所有Kether脚本
- 构造函数接收工作空间目录、脚本文件扩展名和命名空间列表参数
- 使用KetherScriptLoader加载脚本文件，支持标准的Kether语法
- 脚本文件中以"#"开头的行会被视为注释并忽略
- 脚本设置通过特殊的"settings"代码块定义和加载
- 支持自动启动脚本，通过"autostart"设置项控制
- 使用Guava的Multimap管理运行中的脚本，按ID分组
- 脚本执行完成后自动从runningScripts中移除

## 使用场景
> 加载和管理文件系统中的Kether脚本
> 提供脚本的运行时环境和生命周期管理
> 处理脚本的设置和自动启动
> 维护正在运行的脚本状态，支持脚本的终止

## 注意事项
> 目录不存在时会自动创建
> 脚本加载过程中的异常会被捕获并记录，不会中断其他脚本的加载
> 脚本ID使用相对于根目录的路径生成，使用点号(.)替换目录分隔符
> terminateScript方法不会强制终止脚本，而是设置其状态为"已暂停"
> 自动启动的脚本会在loadAll方法中立即启动
