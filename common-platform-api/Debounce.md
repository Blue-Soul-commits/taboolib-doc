# DebounceFunction
## 基本信息 
- 类名和包路径: taboolib.common.function.DebounceFunction
- 基本用途: 提供防抖功能的实现，用于限制函数在短时间内的重复调用
- 类型: Kotlin 抽象类及其子类，以及顶层函数
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> allDebounceFunctions: CopyOnWriteArrayList<DebounceFunction<*>> -> 存储所有创建的防抖函数实例

### 公开静态方法 
> addDebounceFunction(debounceFunction: DebounceFunction<*>): Unit -> 将防抖函数添加到全局列表中
> debounce(delay: Long, async: Boolean = !isPrimaryThread, action: () -> Unit = { }): DebounceFunction.Singleton -> 创建一个简单的无键防抖函数
> debounce<K: Any>(delay: Long, async: Boolean = !isPrimaryThread, action: (K) -> Unit = { _ -> }): DebounceFunction.Simple<K> -> 创建一个基础防抖函数
> debounce<K: Any, T>(delay: Long, async: Boolean = !isPrimaryThread, action: (K, T) -> Unit = { _, _ -> }): DebounceFunction.Parameterized<K, T> -> 创建一个带参数的防抖函数

### 类内可被访问字段 
> keyType: Class<K> -> 防抖函数键的类型
> delay: Long -> 防抖延迟时间（毫秒）
> async: Boolean -> 是否异步执行
> futureMap: ConcurrentHashMap<K, PlatformExecutor.PlatformTask> -> 存储键与任务的映射关系

### 类方法
> removeKey(key: Any): Unit -> 移除指定键的防抖任务
> clearAll(): Unit -> 清除所有防抖任务

## 实现细节
- DebounceFunction 是一个抽象类，提供了防抖功能的基本框架
- 包含三个内部类实现不同类型的防抖功能：
  - Singleton: 无键防抖函数，适用于不需要区分对象的场景
  - Simple: 简单防抖函数，根据键区分不同的调用对象
  - Parameterized: 带参数的防抖函数，除了键外还可以传递额外参数
- 使用 ConcurrentHashMap 存储键与任务的映射，保证线程安全
- 使用 CopyOnWriteArrayList 存储所有创建的防抖函数实例
- 通过 submit 函数创建延迟任务，实现防抖功能
- 提供三个顶层函数 debounce，简化防抖函数的创建

## 使用场景 
> 限制用户界面事件的频繁触发，如按钮点击、输入框变化等
> 控制玩家操作的响应频率，如命令执行、物品使用等
> 优化高频事件处理，如方块更新、实体移动等
> 延迟执行需要等待一段时间的操作，如自动保存、延迟消息等

## 注意事项 
> 防抖函数会取消之前未执行的任务，只保留最后一次调用
> 延迟时间单位为毫秒，但内部会转换为游戏 tick（除以 50）
> 异步参数默认根据当前线程是否为主线程自动设置
> 防抖函数会自动添加到全局列表中，可能需要在适当时机清理不再使用的实例
