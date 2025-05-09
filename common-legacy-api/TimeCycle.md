# TimeCycle

## 基本信息
- 类名和包路径: taboolib.common5.TimeCycle
- 基本用途: 提供时间周期管理工具，支持基于时间间隔、每日、每周和每月的周期计算
- 类型: 工具类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> cacheMap: Map<String, TimeCycle> -> 静态缓存映射，存储已创建的 TimeCycle 实例
> type: Type -> 周期类型（TIME、DAY、WEEK、MONTH）
> day: int -> 日期值（用于 WEEK 和 MONTH 类型）
> hour: int -> 小时值
> minute: int -> 分钟值
> time: long -> 时间间隔（毫秒，用于 TIME 类型）
> cacheEnd: Map<Long, Calendar> -> 缓存不同起始时间对应的结束时间
> end: Calendar -> 当前周期的结束时间
> origin: String -> 原始字符串表示

### 类方法
> TimeCycle(time: long): constructor -> 创建基于时间间隔的周期实例
> TimeCycle(hour: int, minute: int): constructor -> 创建基于每日特定时间点的周期实例
> TimeCycle(type: Type, day: int, hour: int, minute: int): constructor -> 创建指定类型的周期实例
> origin(origin: String): TimeCycle -> 设置原始字符串表示并返回自身
> start(start: long): TimeCycle -> 设置起始时间并计算结束时间，返回自身
> isTimeout(start: long): boolean -> 检查从指定起始时间开始的周期是否已超时
> isTimeout(): boolean -> 检查当前周期是否已超时
> isEquals(): boolean -> 检查当前时间是否与周期设定的时间点相等
> getType(): Type -> 获取周期类型
> getDay(): int -> 获取日期值
> getHour(): int -> 获取小时值
> getMinute(): int -> 获取分钟值
> getTime(): long -> 获取时间间隔
> getOrigin(): String -> 获取原始字符串表示
> getEnd(): Calendar -> 获取周期结束时间
> toString(): String -> 获取对象的字符串表示

## 实现细节
- 支持四种周期类型：固定时间间隔、每日特定时间、每周特定时间和每月特定日期
- 使用 Calendar 类进行日期时间计算和比较
- 实现了缓存机制，相同起始时间的结束时间计算结果会被缓存
- 对于非 TIME 类型的周期，如果当前时间已经超过了今天/本周/本月的设定时间点，会自动计算下一个周期
- 支持链式调用，方便进行连续配置

## 使用场景
> 游戏内定时活动系统，如每日签到、每周任务、每月奖励
> 冷却时间管理，如技能冷却、物品使用冷却
> 定时任务调度，在特定时间点执行特定操作
> 数据统计周期管理，如每日、每周、每月的数据重置

## 注意事项
> 对于 WEEK 类型，day 参数对应 Calendar.DAY_OF_WEEK，其中 1 表示周日，2 表示周一，以此类推
> 对于 MONTH 类型，day 参数对应 Calendar.DAY_OF_MONTH，范围为 1-31
> 使用 start 方法设置起始时间后才能正确使用 isTimeout 方法
> 静态缓存映射 cacheMap 虽然定义但未在类中使用，可能是为了外部访问或未来扩展