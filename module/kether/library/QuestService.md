# QuestService

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestService
- 基本用途: 作为 Kether 脚本引擎的核心服务接口，管理脚本的注册、执行和生命周期
- 类型: 泛型接口
- 所属模块: minecraft-kether

## 类结构
### 公开静态方法
> instance(): QuestService<C> -> 获取全局单例的 QuestService 实例

### 接口方法
> getRegistry(): QuestRegistry -> 获取脚本动作注册表
> getQuest(String id): Optional<Quest> -> 根据 ID 获取脚本
> getQuestSettings(String id): Map<String, Object> -> 获取指定脚本的配置信息
> getQuests(): Map<String, Quest> -> 获取所有已注册的脚本
> startQuest(CTX context): void -> 启动一个脚本执行上下文
> terminateQuest(CTX context): void -> 终止一个脚本执行上下文
> getRunningQuests(): Multimap<String, CTX> -> 获取所有正在运行的脚本上下文
> getRunningQuests(String playerIdentifier): List<CTX> -> 获取指定玩家的所有正在运行的脚本上下文
> getExecutor(): Executor -> 获取同步任务执行器
> getAsyncExecutor(): ScheduledExecutorService -> 获取异步任务执行器
> getLocalizedText(String node, Object... params): String -> 获取本地化文本

## 实现细节
- 接口使用泛型 CTX 参数，CTX 必须是 QuestContext 的子类型
- QuestService 的实现类通常是单例的，通过 ServiceHolder 访问全局实例
- 静态方法 instance() 返回当前已注册的 QuestService 实例，使用了类型转换
- 主要实现类是 ScriptService，它提供了具体的脚本管理和执行功能

## 使用场景
> 作为 Kether 脚本引擎的核心服务，管理脚本的生命周期
> 注册和获取脚本动作解析器
> 启动和终止脚本执行
> 获取本地化的错误或提示信息

## 注意事项
> 使用前必须确保已初始化并注册了 QuestService 实例到 ServiceHolder
> 脚本执行依赖同步和异步执行器，需要正确管理资源
> 本地化文本系统依赖配置文件，用于提供友好的错误信息
