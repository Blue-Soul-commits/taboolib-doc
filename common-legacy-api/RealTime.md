# RealTime

## 基本信息
- 类名和包路径: taboolib.common5.RealTime
- 基本用途: 提供基于真实时间的周期计算工具，支持不同的周起始日设置
- 类型: 枚举类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> START_IN_SUNDAY: RealTime -> 以周日为一周的开始（美国标准）的时间计算模式
> START_IN_MONDAY: RealTime -> 以周一为一周的开始（国际标准）的时间计算模式

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> next: Function<NextTime, Long> -> 计算下一个时间点的函数

### 类方法
> RealTime(next: Function<NextTime, Long>): constructor -> 创建 RealTime 枚举实例
> nextTime(unit: Type, value: int): long -> 获取下一周期的起始时间戳（毫秒）

## 实现细节
- 使用 Java Calendar 类进行日期时间计算
- 提供两种不同的周起始日计算模式：周日起始和周一起始
- 支持三种时间单位：小时、天和周
- 计算下一周期时会重置较小的时间单位（如计算下一天时会重置小时、分钟和秒）
- 使用函数式接口实现不同计算模式的逻辑

## 使用场景
> 定时任务系统，计算下一次执行时间
> 活动系统，计算下一个活动周期的开始时间
> 统计系统，按小时、天或周进行数据统计
> 日历系统，根据不同国家/地区标准计算周起始日

## 注意事项
> START_IN_SUNDAY 和 START_IN_MONDAY 在计算小时和天时逻辑相同，只在计算周时有区别
> 计算结果为毫秒级时间戳，可直接用于 System.currentTimeMillis() 的比较
> 计算下一周期时会重置较小的时间单位，例如计算下一天会将时分秒设为 0
> 传入的 value 参数表示要计算的是第几个下一周期，例如 value=2 表示下下个周期
