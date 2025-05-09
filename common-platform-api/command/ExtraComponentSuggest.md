# ExtraComponentSuggest

## 基本信息
- 类名和包路径: taboolib.common.platform.command.ExtraComponentSuggest
- 基本用途: 提供命令组件的参数补全扩展函数，用于为命令参数提供智能提示
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: TabooLib 平台命令模块

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> suggest(suggest: SuggestContext<ProxyCommandSender>.() -> List<String>?): CommandComponentDynamic -> 创建参数补全
> suggestUncheck(suggest: SuggestContext<ProxyCommandSender>.() -> List<String>?): CommandComponentDynamic -> 创建不检查的参数补全
> suggestBoolean(): CommandComponentDynamic -> 创建布尔值参数补全
> suggestPlayers(suggest: List<String>): CommandComponentDynamic -> 创建在线玩家名称参数补全
> suggestWorlds(suggest: List<String>): CommandComponentDynamic -> 创建世界名称参数补全

### 类内可被访问字段
> 无类内可被访问字段（文件级扩展函数）

### 类方法
> 无类方法（文件级扩展函数）

## 实现细节
- 所有函数都是 CommandComponentDynamic 的扩展函数，返回 CommandComponentDynamic 类型，支持链式调用
- suggest 函数创建标准参数补全，会检查用户输入是否匹配建议列表
- suggestUncheck 函数创建不检查的参数补全，允许用户输入不在建议列表中的值
- suggestBoolean 函数提供布尔值相关的建议列表，包括 "true", "false", "t", "f", "1", "0"
- suggestPlayers 函数提供在线玩家名称的建议列表，可以添加额外的建议
- suggestWorlds 函数提供世界名称的建议列表，可以添加额外的建议
- 所有函数都通过调用 suggestion 方法创建建议，使用 ProxyCommandSender 作为发送者类型
- 使用 SuggestContext 包装发送者和命令上下文，提供更简洁的 API

## 使用场景
> 为命令参数提供智能提示，提高用户体验
> 限制用户输入的选项范围，减少错误输入
> 提供动态生成的建议列表，如在线玩家、可用世界等
> 与 ExtraComponent 中的函数配合使用，为动态参数添加建议
> 在自定义命令组件时手动添加参数补全

## 注意事项
> suggest 函数会检查用户输入是否匹配建议列表，不匹配的输入可能被拒绝
> suggestUncheck 函数不检查用户输入，允许任何值，但仍提供建议列表
> 建议和约束是互斥的，设置建议会覆盖之前设置的约束
> suggestPlayers 和 suggestWorlds 函数会动态获取当前在线玩家和可用世界
> 可以通过 suggest 参数添加额外的建议，这些建议会追加到自动生成的列表后面
> 在 ExtraComponent 中的 int、decimal、bool 等函数内部已经使用了这些建议函数
