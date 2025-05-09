# BukkitServer
## 基本信息
- 类名和包路径: taboolib.platform.util.BukkitServer
- 基本用途: 提供对Bukkit服务器常用功能的简便访问
- 类型: Kotlin属性和扩展函数集合
- 所属模块: bukkit-util

## 类结构
### 公开静态字段
> onlinePlayers: List<Player> -> 获取所有在线玩家的列表

### 公开静态方法
> Any?.broadcast(): Int -> 将任意对象作为字符串广播给所有玩家和控制台，返回接收消息的玩家数量

## 实现细节
- onlinePlayers属性是对Bukkit.getOnlinePlayers()的封装，确保返回一个List<Player>类型
- broadcast()扩展函数允许任何对象（包括null）调用，会将对象转换为字符串后广播
- 使用Bukkit.broadcastMessage()实现广播功能，该方法会向所有玩家和控制台发送消息
- 导入了org.tabooproject.reflex.Reflex用于可能的反射操作，但在当前代码中未直接使用

## 使用场景
> 获取服务器所有在线玩家进行批量操作
> 向服务器所有玩家和控制台广播通知或公告
> 在不需要特定格式的情况下快速发送消息
> 在工具类或静态上下文中访问服务器状态

## 注意事项
> onlinePlayers返回的是一个新的List，对该列表的修改不会影响原始集合
> broadcast()方法会对null对象调用toString()，结果为"null"字符串
> 在高频调用场景中，应避免频繁调用onlinePlayers以减少创建新列表的开销
> broadcast()返回的整数表示接收到消息的玩家数量，可用于确认消息发送状态

