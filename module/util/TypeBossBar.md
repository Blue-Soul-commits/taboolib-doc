# TypeBossBar
## 基本信息
- 类名和包路径: taboolib.platform.lang.TypeBossBar
- 基本用途: 实现Type接口，用于在Bukkit平台上显示BossBar消息
- 类型: 类
- 所属模块: bukkit-util

## 类结构
### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> text: String? -> BossBar显示的文本内容，可为null
> color: BarColor -> BossBar的颜色，默认为WHITE
> style: BarStyle -> BossBar的样式，默认为SOLID
> step: Double -> 进度条每次更新的步长，默认为0.01
> period: Long -> 进度条更新的周期(tick)，默认为2
> method: String -> 进度条的变化方式，可以是"INCREASE"或"DECREASE"，默认为"INCREASE"

### 类方法
> init(source: Map<String, Any>): Unit -> 从配置源初始化BossBar参数
> send(sender: ProxyCommandSender, vararg args: Any): Unit -> 向指定接收者发送BossBar消息
> toString(): String -> 重写的toString方法，返回类的字符串表示

## 实现细节
- TypeBossBar实现了Type接口，专门用于在Bukkit平台上显示BossBar消息
- init方法从配置中加载BossBar参数：
  - text: BossBar显示的文本内容
  - color: BossBar的颜色，通过名称匹配BarColor枚举值
  - style: BossBar的样式，通过名称匹配BarStyle枚举值
  - step: 进度条每次更新的步长
  - period: 进度条更新的周期(tick)
  - method: 进度条的变化方式，只能是"INCREASE"或"DECREASE"
- init方法包含合法性检查，如果text为null或method不合法，会输出警告
- send方法根据接收者类型决定行为：
  - 如果text为null，直接返回
  - 如果接收者是ProxyPlayer，创建BossBar并显示给玩家
  - 如果接收者不是ProxyPlayer，发送toString()的结果作为消息
- BossBar的进度条会根据method、step和period参数动态变化：
  - INCREASE: 从0开始，每次增加step，直到超过1.0
  - DECREASE: 从1开始，每次减少step，直到小于0.0
- 当进度条超出范围(0.0-1.0)时，BossBar会被移除，任务会被取消
- TypeBossBarLoader是一个内部对象，用于在Bukkit平台上注册TypeBossBar类型

## 使用场景
> 在配置文件中定义BossBar消息
> 向玩家显示带有进度条的重要通知或状态信息
> 创建动态变化的进度条效果，如倒计时、加载进度等
> 作为Language系统中的特殊消息类型，提供更丰富的消息展示方式
> 在游戏事件(如副本开始、结束)中显示醒目的提示

## 注意事项
> text字段可能为null，send方法会在text为null时直接返回
> 只有在Bukkit平台上才能正常工作，其他平台会退化为普通消息
> method参数只接受"INCREASE"或"DECREASE"两个值，其他值会触发警告
> BossBar的进度条会根据step和period参数动态变化，直到超出范围
> 进度条更新使用TabooLib的submit函数，依赖于TabooLib的调度系统
