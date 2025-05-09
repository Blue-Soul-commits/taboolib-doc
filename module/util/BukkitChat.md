# BukkitChat
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitChat (文件级扩展函数和内部对象)
- 基本用途: 提供捕获玩家聊天消息的功能，用于实现简单的聊天交互
- 类型: Kotlin 扩展函数和内部监听器对象
- 所属模块: bukkit-util

## 类结构
### 公开静态方法
> Player.nextChat(function: (message: String) -> Unit): Unit -> 捕获玩家下一条聊天消息
> Player.nextChat(function: (message: String) -> Unit, reuse: (player: Player) -> Unit = {}): Unit -> 捕获玩家下一条聊天消息，可处理重复注册情况
> Player.nextChatInTick(tick: Long, func: (message: String) -> Unit, timeout: (player: Player) -> Unit = {}, reuse: (player: Player) -> Unit = {}): Unit -> 在指定时间内捕获玩家聊天消息，超时后执行回调
> Player.cancelNextChat(execute: Boolean = true): Unit -> 取消对玩家聊天消息的捕获，可选择是否执行回调

### 类内可被访问字段
> ChatListener.inputs: ConcurrentHashMap<String, (String) -> Unit> -> 存储玩家名称与对应回调函数的映射

### 类方法
> ChatListener.e(e: PlayerQuitEvent): Unit -> 处理玩家退出事件，清理相关监听器
> ChatListener.e(e: AsyncPlayerChatEvent): Unit -> 处理玩家聊天事件，执行对应回调并取消事件

## 实现细节
- 使用 ConcurrentHashMap 存储玩家名称与回调函数的映射，确保线程安全
- 通过监听 AsyncPlayerChatEvent 事件捕获玩家的聊天消息
- 当捕获到目标玩家的消息时，会取消该聊天事件，防止消息被广播
- 在玩家退出服务器时自动清理相关监听器
- nextChatInTick 方法使用 submit 函数实现延迟任务，用于超时处理

## 使用场景
> 实现简单的命令确认机制，如"输入 YES 确认删除"
> 创建基于聊天的表单或问答系统
> 实现游戏内的对话或交互系统
> 收集玩家的简短文本输入

## 注意事项
> 同一时间只能有一个函数捕获特定玩家的聊天消息
> 如果重复注册捕获函数，默认会调用 reuse 回调而不是覆盖原有函数
> 捕获的聊天消息会被取消广播，其他玩家不会看到
> 玩家退出服务器时会自动清理相关监听器
> cancelNextChat 方法默认会执行回调函数，传入空字符串
