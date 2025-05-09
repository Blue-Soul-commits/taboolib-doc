# ProxyPlayer
## 基本信息 
- 类名和包路径: taboolib.common.platform.ProxyPlayer
- 基本用途: 玩家对象的跨平台抽象接口，提供统一的玩家操作和属性访问方法
- 类型: Kotlin 接口，继承自 ProxyCommandSender
- 所属模块: common-platform-api

## 类结构 
### 公开静态字段 
> 无公开静态字段

### 公开静态方法 
> 无公开静态方法

### 类内可被访问字段 
> address: InetSocketAddress? -> 玩家的网络地址
> uniqueId: UUID -> 玩家的唯一标识符
> ping: Int -> 玩家的网络延迟
> locale: String -> 玩家的客户端语言
> world: String -> 玩家所在的世界名称
> location: Location -> 玩家的当前位置
> compassTarget: Location -> 玩家指南针指向的位置，可读写
> bedSpawnLocation: Location? -> 玩家的床重生点位置，可读写
> displayName: String? -> 玩家的显示名称，可读写
> playerListName: String? -> 玩家在玩家列表中的名称，可读写
> gameMode: ProxyGameMode -> 玩家的游戏模式，可读写
> isSneaking: Boolean -> 玩家是否正在潜行
> isSprinting: Boolean -> 玩家是否正在疾跑
> isBlocking: Boolean -> 玩家是否正在格挡
> isGliding: Boolean -> 玩家是否正在滑翔，可读写
> isGlowing: Boolean -> 玩家是否发光，可读写
> isSwimming: Boolean -> 玩家是否正在游泳，可读写
> isRiptiding: Boolean -> 玩家是否正在使用激流
> isSleeping: Boolean -> 玩家是否正在睡觉
> sleepTicks: Int -> 玩家的睡眠时间（以 tick 为单位）
> isSleepingIgnored: Boolean -> 玩家是否忽略睡眠限制，可读写
> isDead: Boolean -> 玩家是否已死亡
> isConversing: Boolean -> 玩家是否正在对话
> isLeashed: Boolean -> 玩家是否被拴绳牵引
> isOnGround: Boolean -> 玩家是否在地面上
> isInsideVehicle: Boolean -> 玩家是否在载具内
> hasGravity: Boolean -> 玩家是否受重力影响，可读写
> attackCooldown: Int -> 玩家的攻击冷却时间
> playerTime: Long -> 玩家的游戏时间，可读写
> firstPlayed: Long -> 玩家首次加入服务器的时间
> lastPlayed: Long -> 玩家最后一次加入服务器的时间
> absorptionAmount: Double -> 玩家的额外生命值，可读写
> noDamageTicks: Int -> 玩家的无敌时间，可读写
> remainingAir: Int -> 玩家的剩余氧气，可读写
> maximumAir: Int -> 玩家的最大氧气值
> level: Int -> 玩家的经验等级，可读写
> exp: Float -> 玩家的经验值，可读写
> exhaustion: Float -> 玩家的疲劳值，可读写
> saturation: Float -> 玩家的饱食度，可读写
> foodLevel: Int -> 玩家的饥饿值，可读写
> health: Double -> 玩家的生命值，可读写
> maxHealth: Double -> 玩家的最大生命值，可读写
> allowFlight: Boolean -> 玩家是否允许飞行，可读写
> isFlying: Boolean -> 玩家是否正在飞行，可读写
> flySpeed: Float -> 玩家的飞行速度，可读写
> walkSpeed: Float -> 玩家的行走速度，可读写
> pose: String -> 玩家的姿势状态
> facing: String -> 玩家的朝向

### 类方法
> kick(message: String?): Unit -> 将玩家踢出服务器，可指定原因
> chat(message: String): Unit -> 让玩家发送聊天消息
> playSound(location: Location, sound: String, volume: Float, pitch: Float): Unit -> 为玩家播放音效
> playSoundResource(location: Location, sound: String, volume: Float, pitch: Float): Unit -> 为玩家播放资源包中的音效
> sendTitle(title: String?, subtitle: String?, fadein: Int, stay: Int, fadeout: Int): Unit -> 向玩家发送标题和副标题
> sendActionBar(message: String): Unit -> 向玩家发送动作栏消息
> sendRawMessage(message: String): Unit -> 向玩家发送原始 JSON 格式消息
> sendParticle(particle: String, location: Location, offset: Vector, count: Int, speed: Double, data: Any?): Unit -> 向玩家发送粒子效果
> teleport(location: Location): Unit -> 将玩家传送到指定位置
> giveExp(exp: Int): Unit -> 给予玩家经验值
> onQuit(callback: Runnable): Unit -> 注册玩家退出游戏时的回调函数

## 实现细节
- 继承自 ProxyCommandSender 接口，拥有命令发送者的所有功能
- 作为跨平台抽象接口，隐藏了不同平台（如 Bukkit、Bungee、Velocity 等）玩家对象的具体实现
- 提供了丰富的玩家属性访问和操作方法，涵盖了游戏中玩家的各种状态和行为
- 实现类通常由 TabooLib 内部提供，针对不同平台有不同的实现

## 使用场景 
> 在跨平台插件中操作玩家，无需关心具体平台
> 获取和修改玩家的各种属性，如位置、游戏模式、生命值等
> 向玩家发送各种形式的消息，如聊天消息、标题、动作栏等
> 对玩家执行各种操作，如传送、播放音效、踢出服务器等

## 注意事项 
> 某些属性和方法在特定平台可能不完全支持，使用前应考虑平台兼容性
> 修改玩家属性时应注意游戏平衡和服务器规则
> onQuit 方法注册的回调无法取消，应谨慎使用
> 在多线程环境中操作玩家对象时，应注意线程安全问题