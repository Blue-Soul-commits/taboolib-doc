# BukkitBook
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitBook (文件级扩展函数和内部对象)
- 基本用途: 提供向玩家发送可编辑书本并捕获编辑动作的功能
- 类型: Kotlin 扩展函数和内部监听器对象
- 所属模块: bukkit-util

## 类结构
### 公开静态方法
> Player.inputBook(display: String, disposable: Boolean = true, content: List<String> = emptyList(), catcher: (List<String>) -> Unit): Unit -> 向玩家发送一本可编辑的书并捕获编辑动作

### 类内可被访问字段
> BookListener.regex: Array<String> -> 用于标识书本的特殊文本数组
> BookListener.inputs: ConcurrentHashMap<String, (List<String>) -> Unit> -> 存储玩家名称与对应回调函数的映射

### 类方法
> BookListener.onPlayerEditBookEvent(event: PlayerEditBookEvent): Unit -> 处理玩家编辑书本事件的监听器方法

## 实现细节
- 使用 `buildBook` 函数创建一本可编辑的书本（WRITABLE_BOOK）
- 通过在书本的 lore 中添加特殊标记来识别由此功能创建的书本
- 使用 ConcurrentHashMap 存储玩家名称与回调函数的映射，确保线程安全
- 监听 PlayerEditBookEvent 事件来捕获玩家的编辑动作
- 根据书本 lore 中的标记决定是否在编辑后销毁书本

## 使用场景
> 收集玩家的长文本输入，如游戏内的反馈、申请或故事创作
> 创建可编辑的游戏内笔记或日记系统
> 实现需要多行文本输入的表单界面

## 注意事项
> 如果玩家已经持有带有相同标记的书本，会先移除这些书本
> 书本可以设置为一次性使用（disposable=true）或可重复使用（disposable=false）
> 编辑后的内容会通过 TextComponent 转换为纯文本，并按换行符分割为多行
> 使用了 submit(delay = 1) 延迟一个 tick 移除一次性书本，避免与事件处理冲突
