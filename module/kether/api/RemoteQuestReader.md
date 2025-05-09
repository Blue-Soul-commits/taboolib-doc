# RemoteQuestReader

## 基本信息
- 类名和包路径: taboolib.module.kether.RemoteQuestReader
- 基本用途: Kether脚本引擎的远程读取器封装，实现跨插件/容器读取和解析脚本
- 类型: 类
- 所属模块: kether

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> remote: OpenContainer -> 远程容器实例，用于进行跨容器通信
> source: Any -> 远程QuestReader对象的原始引用

### 类方法
> peek(): Char -> 查看当前字符
> peek(n: Int): Char -> 查看指定偏移量的字符
> getIndex(): Int -> 获取当前读取索引
> getMark(): Int -> 获取标记位置
> hasNext(): Boolean -> 检查是否有更多内容
> nextToken(): String -> 读取下一个标记
> mark(): Unit -> 标记当前位置
> reset(): Unit -> 重置到标记位置
> nextAction<T>(): ParsedAction<T> -> 读取下一个动作
> nextAction<T>(namespace: String?): ParsedAction<T> -> 读取指定命名空间下的下一个动作
> expect(value: String): Unit -> 期望下一个标记为指定值

## 实现细节
- RemoteQuestReader实现了QuestReader接口，封装了对远程脚本读取器的操作
- 所有基本读取方法(peek, getIndex, nextToken等)通过反射调用远程源对象的对应方法
- nextAction方法需要特殊处理，将远程返回的动作包装为RemoteQuestAction
- 使用getProperty获取远程ParsedAction的属性，重新构建本地ParsedAction对象
- nextAction(namespace)方法增加了异常处理，当远程不支持该重载方法时回退到无参版本
- 所有反射调用都使用remap=false，避免字段名映射问题

## 使用场景
> 跨插件读取和解析Kether脚本
> 在不同ClassLoader环境下共享脚本解析功能
> 实现模块化的脚本系统，一个插件可以解析另一个插件的脚本
> 与RemoteActionParser和RemoteQuestAction配合，构建完整的远程脚本系统

## 注意事项
> 使用反射调用，可能存在性能开销
> 依赖远程容器的可用性，如果远程容器不可用则操作失败
> nextAction方法需要正确处理远程动作和属性，确保跨容器传递
> 对于nextAction(namespace)方法，使用try-catch处理可能的方法不存在异常
> 远程解析的动作会被包装为本地ParsedAction对象，但内部包含RemoteQuestAction
