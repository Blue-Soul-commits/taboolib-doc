# QuestLoader

## 基本信息
- 类名和包路径: taboolib.library.kether.QuestLoader
- 基本用途: 负责从文件或字节数据中加载 Kether 脚本
- 类型: 接口
- 所属模块: minecraft-kether

## 类结构
### 默认方法
> load(QuestService<C> service, String id, byte[] bytes): Quest -> 从字节数组加载脚本，使用默认空命名空间

### 接口方法
> load(QuestService<C> service, String id, Path path, List<String> namespace): Quest -> 从文件路径加载脚本
> load(QuestService<C> service, String id, byte[] bytes, List<String> namespace): Quest -> 从字节数组加载脚本，指定命名空间

## 实现细节
- 接口使用泛型 C 参数，C 必须是 QuestContext 的子类型
- 主要实现类是 SimpleQuestLoader，提供了基础的脚本加载功能
- KetherScriptLoader 扩展了 SimpleQuestLoader，增加了特定的脚本解析功能
- 脚本加载过程使用 BlockReader 和 SimpleReader 进行词法和语法分析

## 使用场景
> 从文件系统中加载 Kether 脚本文件
> 从字符串或字节数组创建临时脚本
> 在工作区（Workspace）中批量加载脚本文件

## 注意事项
> 加载脚本时需要提供 QuestService 实例和脚本 ID
> 命名空间参数用于解析脚本中的动作引用
> 可能抛出 LocalizedException 或 IOException 异常，需要正确处理
