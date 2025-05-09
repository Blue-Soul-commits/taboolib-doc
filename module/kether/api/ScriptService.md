# ScriptService

## 基本信息
- 类名和包路径: taboolib.module.kether.ScriptService
- 基本用途: Kether脚本引擎的核心服务实现，管理脚本的注册、执行和生命周期
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> locale: Configuration -> 本地化配置文件，通过@Config注解加载自"kether.yml"
> mainspace: Workspace -> 懒加载的主工作空间，位于插件数据文件夹的"kether"目录

### 公开静态方法
> 无

### 类内可被访问字段
> registry: DefaultRegistry -> 脚本动作注册表实例
> syncExecutor: ScriptSchedulerExecutor -> 同步任务执行器
> asyncExecutor: ScheduledExecutorService -> 异步任务执行器，使用2个线程的线程池

### 类方法
> getRegistry(): QuestRegistry -> 获取脚本动作注册表
> getQuest(id: String): Optional<Script> -> 根据ID获取脚本
> getQuestSettings(id: String): Map<String, Any?> -> 获取指定脚本的配置信息
> getQuests(): Map<String, Script> -> 获取所有已注册的脚本
> getRunningQuests(): Multimap<String, ScriptContext> -> 获取所有正在运行的脚本上下文
> getRunningQuests(playerIdentifier: String): List<ScriptContext> -> 获取指定玩家的所有正在运行的脚本上下文
> getExecutor(): Executor -> 获取同步任务执行器
> getAsyncExecutor(): ScheduledExecutorService -> 获取异步任务执行器
> getLocalizedText(node: String, vararg params: Any): String -> 获取本地化文本
> startQuest(context: ScriptContext) -> 启动一个脚本执行上下文
> terminateQuest(context: ScriptContext) -> 终止一个脚本执行上下文

## 实现细节
- ScriptService实现了QuestService<ScriptContext>接口，提供了Kether脚本引擎的核心功能
- 使用@Inject注解标记为自动注入的单例
- 在初始化块中调用ServiceHolder.setQuestServiceInstance(this)，将自身注册为全局服务实例
- 使用DefaultRegistry作为脚本动作注册表实现
- 同步执行器使用ScriptSchedulerExecutor，确保任务在主线程执行
- 异步执行器使用固定大小(2)的线程池
- 通过@Config注解加载本地化配置文件
- 使用mainspace(Workspace)管理脚本的加载和执行
- 本地化文本支持参数替换，使用replaceWithOrder函数

## 使用场景
> 作为Kether脚本引擎的核心服务，管理脚本的生命周期
> 提供脚本的注册、获取和执行功能
> 获取本地化的错误或提示信息
> 管理脚本的执行上下文和运行状态

## 注意事项
> 服务在初始化时会自动注册为全局单例，确保唯一性
> locale变量使用lateinit修饰，使用前应确保已初始化
> mainspace是懒加载的，首次访问时会创建工作空间
> 异步执行器使用固定大小的线程池，注意资源管理和可能的线程饥饿问题
> getLocalizedText方法在locale未初始化时会返回格式化的节点名和参数
