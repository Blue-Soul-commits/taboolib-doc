# QuestActionParser

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestActionParser
- 基本用途: 负责将 QuestReader 中读取的脚本内容解析为可执行的 QuestAction
- 类型: 接口
- 所属模块: minecraft-kether

## 类结构
### 公开静态方法
> of(Function<QuestReader, QuestAction<T>> resolveFunction): QuestActionParser -> 创建一个 QuestActionParser 实例，使用提供的函数进行解析

### 接口方法
> resolve(@NotNull QuestReader resolver): QuestAction<T> -> 从提供的 QuestReader 中解析并创建 QuestAction 实例

## 实现细节
- 接口设计为泛型接口，可以解析出任意类型的 QuestAction
- 静态工厂方法 of() 提供了便捷的方式创建 QuestActionParser 实例
- 实现类需要从 QuestReader 中读取并解析脚本片段，转换为对应的 QuestAction

## 使用场景
> 在 Kether 脚本引擎中注册新的动作解析器
> 扩展 Kether 脚本语言，添加自定义语法和功能
> 作为 QuestRegistry 的组件，用于将脚本文本解析为可执行的动作

## 注意事项
> resolve 方法返回的 QuestAction 会被封装在 ParsedAction 中执行
> 实现类需要正确处理泛型类型转换和类型安全问题
