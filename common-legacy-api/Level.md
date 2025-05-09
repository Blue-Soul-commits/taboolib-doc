# Level

## 基本信息
- 类名和包路径: taboolib.common5.Level
- 基本用途: 提供 Minecraft 玩家经验和等级相关的计算工具
- 类型: 工具类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> setTotalExperience(player: ProxyPlayer, exp: int): void -> 设置玩家的当前经验总值
> getExpAtLevel(level: int): int -> 获取指定等级下的最大经验值
> getExpToLevel(level: int): int -> 获取达到指定等级所需的经验总值
> getTotalExperience(player: ProxyPlayer): int -> 获取玩家当前的经验总值
> getExpUntilNextLevel(player: ProxyPlayer): int -> 获取玩家距离升级还差多少经验

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> getExpAtLevel(player: ProxyPlayer): int -> 私有方法，获取玩家当前等级下的最大经验值

## 实现细节
- 经验计算基于 Minecraft 的经验系统规则，根据等级范围使用不同的计算公式
- 等级 1-15：(2 * level) + 7
- 等级 16-30：(5 * level) - 38
- 等级 31+：(9 * level) - 158
- 在计算总经验时，会累加每个等级所需的经验值
- 防止经验值溢出，当计算结果为负数时返回 Integer.MAX_VALUE

## 使用场景
> 玩家经验管理系统，精确控制玩家的经验和等级
> 自定义技能或成就系统，需要根据玩家经验值计算奖励
> 游戏平衡性调整，分析玩家升级所需经验曲线
> RPG 插件中的等级和经验系统实现

## 注意事项
> 经验计算公式基于 Minecraft 的标准规则，如果游戏版本更新可能需要调整
> 当经验值过大时，可能会发生整数溢出，此时会返回 Integer.MAX_VALUE
> 该类使用 ProxyPlayer 接口，适用于跨平台的 TabooLib 环境
> 注释中提到 Bukkit 和 Nukkit 两种算法，但代码中只实现了一种算法
