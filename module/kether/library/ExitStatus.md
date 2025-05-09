# ExitStatus

## 基本信息
- 类名和包路径: taboolib.library.kether.ExitStatus
- 基本用途: 表示 Kether 脚本执行的状态，包括运行状态、等待状态和时间控制
- 类型: 类
- 所属模块: minecraft-kether

## 类结构
### 公开静态字段
> PAUSED: ExitStatus -> 表示脚本已暂停的预定义状态（运行中但不等待）

### 公开静态方法
> success(): ExitStatus -> 创建表示成功完成的状态（不运行且不等待）
> paused(): ExitStatus -> 返回表示暂停状态的预定义实例
> cooldown(timeout: long): ExitStatus -> 创建等待冷却的状态，包括开始时间和超时时间

### 类内可被访问字段
> running: boolean -> 表示脚本是否仍在运行中
> waiting: boolean -> 表示脚本是否处于等待状态
> startTime: long -> 表示等待开始的时间戳（用于冷却时间计算）

### 类方法
> ExitStatus(running: boolean, waiting: boolean, startTime: long) -> 构造函数，创建具有指定运行状态、等待状态和开始时间的实例
> isRunning(): boolean -> 返回脚本是否仍在运行中
> isWaiting(): boolean -> 返回脚本是否处于等待状态
> getStartTime(): long -> 获取等待开始的时间戳
> equals(o: Object): boolean -> 比较两个 ExitStatus 对象是否相等
> hashCode(): int -> 生成对象的哈希码
> toString(): String -> 返回对象的字符串表示

## 实现细节
- ExitStatus 是一个不可变类，所有字段都是 final 的
- 提供了三种预定义状态：success（成功完成）、paused（暂停）和 cooldown（冷却等待）
- cooldown 方法接受一个 timeout 参数，用于计算冷却等待的结束时间
- startTime 字段在 cooldown 方法中被设置为当前系统时间加上超时时间

## 使用场景
> 表示 Kether 脚本执行的当前状态
> 控制脚本的执行流程，如暂停、终止或等待
> 实现脚本的冷却时间机制，如延迟执行或定时任务
> 由 QuestContext 使用，用于跟踪和管理脚本执行状态

## 注意事项
> 脚本执行引擎会检查 ExitStatus 来决定是否继续执行脚本
> waiting 为 true 且 running 为 true 表示脚本处于冷却等待状态
> 当使用 cooldown 创建状态时，startTime 字段表示的是冷却结束的时间戳，而不是开始时间
