# NMSScoreboard

## 基本信息
- 类名和包路径: taboolib.module.nms.NMSScoreboard
- 基本用途: 提供跨版本的记分板操作功能
- 类型: 抽象类
- 所属模块: bukkit-nms-stable

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> setupScoreboard(player: Player, color: Boolean, title: String): Unit -> 初始化记分板
> setDisplayName(player: Player, title: String): Unit -> 设置记分板标题
> changeContent(player: Player, content: List<String>, lastContent: Map<Int, String>): Boolean -> 修改记分板内容
> display(player: Player): Unit -> 显示记分板
> updateTeam(player: Player, prefix: String, suffix: String, color: ChatColorFormat, createTeam: Boolean, target: Player?): Unit -> 更新玩家队伍

## 实现细节
- 使用 `ConcurrentHashMap` 存储玩家记分板缓存
- 提供四个扩展函数简化使用：`Player.sendScoreboard()`、`Player.setPrefix()`、`Player.setSuffix()` 和 `Player.setTeamColor()`
- 使用事件监听器管理记分板生命周期：玩家加入游戏时初始化，离开游戏时清理
- 实现类 `NMSScoreboardImpl` 根据不同的 Minecraft 版本使用不同的方法操作记分板
- 支持从 1.8 到 1.21 版本的 Minecraft
- 使用特殊字符作为记分板行的唯一标识符
- 通过反射设置数据包属性，实现跨版本兼容

## 使用场景
> 在需要为玩家显示记分板时使用
> 在需要设置玩家名称前缀、后缀或颜色时使用
> 在插件开发中需要跨版本兼容时使用

## 注意事项
> 记分板最多支持 21 行内容（由 `uniqueOwner` 列表大小决定）
> 在 1.12 及以下版本中，每行内容长度限制为 16 个字符，超出部分会被分割为后缀
> 不同版本的 Minecraft 对记分板的处理方式不同，特别是 1.13+ 和 1.20.2+ 版本
> 使用反射机制，可能会因为 Minecraft 版本更新导致方法或字段名变化而失效
