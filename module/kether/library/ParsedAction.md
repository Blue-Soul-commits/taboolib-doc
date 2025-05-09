# ParsedAction

## 基本信息
- 类名和包路径: taboolib.library.kether.ParsedAction
- 基本用途: 封装和表示 Kether 脚本中的可执行动作，包含动作对象及其属性
- 类型: 泛型类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> noop(): ParsedAction<T> -> 创建一个不执行任何操作的空动作实例

### 类内可被访问字段
> action: QuestAction<A> -> 封装的具体动作实现
> properties: Map<String, Object> -> 存储动作的额外属性

### 类方法
> ParsedAction(action: QuestAction<A>) -> 构造函数，使用指定动作创建实例，初始化空属性映射
> ParsedAction(action: QuestAction<A>, properties: Map<String, Object>) -> 构造函数，使用指定动作和属性映射创建实例
> process(frame: QuestContext.Frame): CompletableFuture<A> -> 在指定执行帧上处理动作
> get(key: ActionProperty<T>): T -> 获取属性值，如不存在则抛出空指针异常
> get(key: ActionProperty<T>, defaultValue: T): T -> 获取属性值，如不存在则返回默认值
> set(key: ActionProperty<T>, value: T): void -> 设置属性值
> has(key: ActionProperty<T>): boolean -> 检查是否存在指定属性
> getAction(): QuestAction<?> -> 获取封装的动作对象
> getProperties(): Map<String, Object> -> 获取动作的属性映射
> toString(): String -> 返回动作的字符串表示
> equals(o: Object): boolean -> 比较两个 ParsedAction 是否相等
> hashCode(): int -> 计算哈希码

## 实现细节
- 封装了一个具体的 QuestAction 实现，并为其提供属性存储功能
- 提供类型安全的属性访问方法，使用 ActionProperty 类型作为键
- 对于远程动作对象的特殊处理，通过 RemoteQuestAction 支持跨插件通信
- 实现了 equals 和 hashCode 方法，用于在集合中正确比较对象
- 内部类 ActionProperty 提供了类型安全的属性键定义机制

## 使用场景
> 在 Kether 脚本解析过程中表示已解析的动作
> 在动作执行框架中传递动作信息和额外属性
> 作为 Quest.Block 容器中存储的动作单元
> 在远程执行环境中传递动作调用信息

## 注意事项
> 动作属性必须通过 ActionProperty 类型访问，以确保类型安全
> 通过 get() 方法获取不存在的属性会抛出 NullPointerException
> 设置属性值时不能使用 null 值，会抛出 NullPointerException
> 使用预定义的 ActionProperties 常量（如 BLOCK、ADDRESS、REQUIRE_FRAME）来存取标准属性
