# QuestRegistry

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestRegistry
- 基本用途: 注册和管理 Kether 脚本引擎中的动作解析器和字符串处理器
- 类型: 接口
- 所属模块: minecraft-kether

## 类结构
### 接口方法
> registerAction(String id, QuestActionParser parser): void -> 注册动作解析器到默认命名空间
> registerAction(String namespace, String id, QuestActionParser parser): void -> 注册动作解析器到指定命名空间
> registerStringProcessor(String id, BiFunction<QuestContext.Frame, String, String> processor): void -> 注册字符串处理器
> unregisterAction(String id): void -> 从默认命名空间中注销动作解析器
> unregisterAction(String namespace, String id): void -> 从指定命名空间中注销动作解析器
> getRegisteredActions(String namespace): Collection<String> -> 获取指定命名空间中所有已注册的动作ID
> getRegisteredActions(): Collection<String> -> 获取默认命名空间中所有已注册的动作ID
> getRegisteredNamespace(): Collection<String> -> 获取所有已注册的命名空间
> getParser(String id, List<String> namespace): Optional<QuestActionParser> -> 从命名空间列表中获取解析器
> getParser(String id, String namespace): Optional<QuestActionParser> -> 从指定命名空间中获取解析器
> getParser(String id): Optional<QuestActionParser> -> 从默认命名空间中获取解析器
> getStringProcessor(String id): Optional<BiFunction<QuestContext.Frame, String, String>> -> 获取字符串处理器

## 实现细节
- 默认的命名空间为 "kether"
- 动作ID可以包含命名空间前缀，形式为 "namespace:id"
- 接口的主要实现类是 DefaultRegistry，它使用 Map 结构存储解析器和处理器
- 动作解析器从 QuestReader 中解析脚本文本，并创建对应的 QuestAction 实例

## 使用场景
> 注册自定义动作到 Kether 脚本引擎中
> 管理脚本引擎中的动作解析器和字符串处理器
> 扩展 Kether 脚本语言的功能和语法

## 注意事项
> 在注册自定义动作时，应确保动作ID在命名空间中是唯一的
> 动作解析器应正确处理脚本文本，返回有效的 QuestAction 实例
> 通过命名空间可以组织和隔离不同来源的动作解析器