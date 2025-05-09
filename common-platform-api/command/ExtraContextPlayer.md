# ExtraContextPlayer
## 基本信息 
- 类名和包路径: taboolib.common.platform.command.ExtraContextPlayer
- 基本用途: 为 CommandContext 类提供扩展函数，用于获取命令参数并转换为玩家对象
- 类型: Kotlin 扩展函数文件
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无静态字段

### 公开静态方法 
> player(id: String): ProxyPlayer -> 根据节点名称获取输入参数并转换为玩家对象，如果参数或玩家不存在则抛出异常
> playerOrNull(id: String): ProxyPlayer? -> 根据节点名称获取输入参数并转换为玩家对象，如果参数或玩家不存在则返回 null
> players(id: String): List<ProxyPlayer> -> 根据节点名称获取输入参数并转换为玩家列表，如果参数为 "*" 则获取所有在线玩家，否则获取单个玩家
> playersOrNull(id: String): List<ProxyPlayer>? -> 根据节点名称获取输入参数并转换为玩家列表，如果参数或玩家不存在则返回 null

### 类内可被访问字段 
> 无类内字段（扩展函数文件）

### 类方法
> 无类方法（扩展函数文件）

## 实现细节
- 所有扩展函数都是 CommandContext 类的扩展，用于处理命令参数并转换为玩家对象
- 使用 CommandContext 的 get/getOrNull 方法获取原始参数值
- 使用 getProxyPlayer 函数将玩家名称转换为 ProxyPlayer 对象
- 对于 players/playersOrNull 方法，特殊处理了参数值为 "*" 的情况，此时返回所有在线玩家
- 所有方法都会调用 substringBefore(' ') 来处理可能包含空格的参数，只取第一部分作为玩家名

## 使用场景 
> 在命令处理中获取目标玩家
> 创建支持操作多个玩家的命令
> 实现管理类命令，如传送、给予物品等需要指定玩家的操作

## 注意事项 
> player 和 players 方法在玩家不存在时会抛出异常，应当妥善处理
> playerOrNull 和 playersOrNull 方法在玩家不存在时会返回 null，更适合用于可选参数
> players 方法支持使用 "*" 作为特殊参数获取所有在线玩家
> 所有方法都只取参数中第一个空格前的内容作为玩家名