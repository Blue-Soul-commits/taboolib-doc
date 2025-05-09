# LoreMap

## 基本信息
- 类名和包路径: taboolib.common5.LoreMap
- 基本用途: 高效处理 Minecraft 物品 Lore 文本的前缀匹配和对象映射工具
- 类型: 泛型工具类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> root: TrieNode -> 字典树的根节点
> ignorePrefix: boolean -> 是否忽略前缀
> ignoreSpace: boolean -> 是否忽略空格
> ignoreColor: boolean -> 是否忽略颜色代码

### 类方法
> LoreMap(ignoreSpace: boolean, ignoreColor: boolean, ignorePrefix: boolean): constructor -> 创建 LoreMap 实例，指定处理选项
> LoreMap(): constructor -> 创建默认 LoreMap 实例，默认忽略颜色和空格，不忽略前缀
> put(lore: String, value: T): void -> 向 LoreMap 中添加 lore 文本和对应的对象
> get(lore: String): T -> 查询 lore 对应的对象，无则返回 null
> getMatchResult(lore: String): MatchResult<T> -> 获取 lore 的匹配结果，包含匹配对象和剩余文本
> clear(): void -> 清空 LoreMap 中的所有数据

## 实现细节
- 基于字典树（Trie）数据结构实现，提供高效的前缀匹配
- 使用 ConcurrentHashMap 保证线程安全，支持并发访问
- 支持三种文本处理选项：忽略前缀、忽略空格、忽略颜色代码
- 内部使用 LoreChar 类封装字符，提供自定义的哈希和相等性比较
- 通过 MatchResult 类返回匹配结果，包含匹配对象和剩余文本
- 在添加和查询时自动处理 Minecraft 颜色代码（&和§）

## 使用场景
> 物品属性系统，从物品 Lore 中提取属性名称和数值
> 装备识别系统，通过 Lore 前缀快速识别特殊装备类型
> 物品分类系统，根据 Lore 内容对物品进行分类
> 任何需要从大量 Lore 文本中快速匹配特定模式的场景

## 注意事项
> 对于完全匹配的场景，建议使用 HashMap 的 containsKey 方法
> 添加的 Lore 文本会根据设置自动处理颜色代码和空格，实际存储的内容可能与原始文本不同
> 当设置 ignorePrefix=true 时，会从文本开头开始寻找第一个可匹配的字符，适合处理有前缀的 Lore
> 性能优势在处理大量（上百甚至上千条）Lore 文本时最为明显

