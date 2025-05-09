# CommandHelper
## 基本信息
- 类名和包路径: taboolib.expansion.CommandHelper
- 基本用途: 为TabooLib命令系统提供自动生成帮助信息的扩展功能
- 类型: Kotlin文件（包含扩展函数）
- 所属模块: minecraft-command-helper

## 类结构
### 公开静态字段
> 无公开静态字段（文件中只包含扩展函数）

### 公开静态方法
> 无公开静态方法（文件中只包含扩展函数）

### 类内可被访问字段
> 无类内字段（不是类，而是文件）

### 扩展函数
> CommandComponent.createHelper(checkPermissions: Boolean = true): Unit -> 为命令组件创建帮助信息处理器

## 实现细节
- CommandHelper提供了CommandComponent的扩展函数createHelper，用于自动生成命令帮助信息
- createHelper方法接收一个布尔参数checkPermissions，默认为true，用于控制是否检查权限
- 该方法通过execute<ProxyCommandSender>注册一个命令执行器，当命令被执行时生成帮助信息
- 帮助信息生成过程包含以下几个关键部分：
  - check函数：过滤命令组件，根据权限和可见性筛选可用命令
  - space函数：生成指定数量的空格，用于格式化输出
  - print函数：递归打印命令组件及其子组件，构建树形结构的帮助信息
- 支持两种主要的命令组件类型：
  - CommandComponentLiteral：文字命令组件，显示为红色文本
  - CommandComponentDynamic：动态命令组件，显示为灰色尖括号包围的文本
- 对于动态命令组件，支持两种注释格式：
  - 普通文本：直接显示comment属性的值
  - 语言节点：如果comment以@开头，会通过asLangText获取对应的翻译文本
- 可选参数使用灰色方括号表示，通过CommandComponentDynamic的optional属性或父组件的optional状态确定
- 树形结构使用ASCII字符（├──、└──、│）构建，提供清晰的命令层级关系
- 最终生成的帮助信息通过sender.sendMessage发送给命令发送者

## 使用场景
> 在TabooLib命令系统中，为复杂命令自动生成帮助信息
> 在插件开发中，简化命令帮助信息的实现，提供统一的格式
> 支持多语言命令参数描述，通过@前缀引用语言节点
> 根据玩家权限动态过滤可用命令，只显示玩家有权限使用的命令
> 通过树形结构清晰展示命令的层级关系和参数要求

## 注意事项
> createHelper方法应该在命令注册过程中调用，通常在命令构建的最后阶段
> 如果checkPermissions为true，将只显示玩家有权限使用的命令
> CommandComponentLiteral的hidden属性为true的命令将被隐藏，不会显示在帮助信息中
> 动态命令组件的注释如果以@开头，需要确保对应的语言节点存在
> 帮助信息使用Minecraft颜色代码(§)格式化，确保接收者支持颜色代码
