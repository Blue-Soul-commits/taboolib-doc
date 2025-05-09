# Baffle

## 基本信息
- 类名和包路径: taboolib.common5.Baffle
- 基本用途: 提供冷却功能的工具类，可以基于时间或次数进行限制
- 类型: 抽象类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> of(duration: long, timeUnit: TimeUnit): Baffle -> 创建一个基于时间的冷却工具，根据指定的时间间隔限制操作
> of(count: int): Baffle -> 创建一个基于计数的冷却工具，根据指定的次数限制操作

### 类内可被访问字段
> 无类内可被访问字段（在抽象基类中）

### 类方法
> resetAll(): void -> 重置所有数据
> reset(id: String): void -> 重置指定个体的执行缓存
> reset(): void -> 重置全局（"*"）的执行缓存
> next(id: String): void -> 强制更新指定个体的数据
> next(): void -> 强制更新全局（"*"）的数据
> hasNext(id: String, update: boolean): boolean -> 验证个体是否可以执行，并可选择是否更新数据
> hasNext(id: String): boolean -> 验证个体是否可以执行，默认更新数据
> hasNext(): boolean -> 验证全局（"*"）是否可以执行，默认更新数据

## 实现细节
- Baffle 有两个具体实现：BaffleTime（基于时间的冷却）和 BaffleCounter（基于计数的冷却）
- BaffleTime 使用毫秒时间戳记录上次执行时间，并根据设定的时间间隔判断是否可以执行
- BaffleCounter 使用计数器记录执行次数，达到指定次数后才允许执行并重置计数
- 两种实现都支持全局模式（使用"*"作为ID）和个体模式（使用自定义ID）
- 内部使用 ConcurrentHashMap 存储数据，保证线程安全

## 使用场景
> 限制玩家操作频率，防止过于频繁的交互
> 技能冷却系统，控制技能使用间隔
> 消息发送限流，避免消息刷屏
> 任何需要控制操作频率或间隔的场景

## 注意事项
> hasNext 方法默认会在返回 true 时更新数据，如果只想检查而不更新，需要使用 hasNext(id, false)
> 全局模式和个体模式使用不同的存储，互不影响
> BaffleTime 和 BaffleCounter 的 hasNext 方法返回值含义相反，使用时需注意