# PlayerJumpEvent

## 基本信息
- 类名和包路径: taboolib.platform.event.PlayerJumpEvent
- 基本用途: 玩家跳跃事件，用于检测和处理玩家跳跃行为
- 类型: 事件类
- 所属模块: taboolib.module.bukkit.bukkit-util

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> player: Player -> 跳跃的玩家实例
> baffle: Baffle -> 用于控制事件触发频率的节流器，设置为350毫秒

### 类方法
> onMove(e: PlayerMoveEvent): void -> 监听玩家移动事件，检测跳跃行为并触发PlayerJumpEvent
> onQuit(e: PlayerQuitEvent): void -> 监听玩家退出事件，重置对应玩家的节流器状态

## 实现细节
- 继承自CancelableInternalEvent，支持取消事件
- 使用@Inject和@PlatformSide注解标记只在Bukkit平台注入
- 通过监听PlayerMoveEvent来检测玩家跳跃行为
- 使用Baffle节流器防止短时间内重复触发事件
- 跳跃检测基于玩家Y轴坐标变化：
  - 排除飞行和旁观模式的玩家
  - 当Y轴变化不等于0.5且大于0.419时判定为跳跃
- 当事件被取消时，将玩家位置重置回原位置

## 使用场景
> 监听玩家跳跃行为
> 限制玩家在特定区域或状态下的跳跃
> 为跳跃动作添加自定义效果或奖励
> 实现跳跃相关的游戏机制

## 注意事项
> 事件使用了节流器，同一玩家在350毫秒内只会触发一次
> 事件可以被取消，取消后玩家将无法完成跳跃
> 跳跃检测基于Y轴坐标变化，可能受到特殊地形或效果的影响
> 该事件只在Bukkit平台有效，由@PlatformSide(Platform.BUKKIT)注解标记
