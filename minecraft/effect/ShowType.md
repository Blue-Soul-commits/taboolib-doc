# ShowType

## 基本信息
- 类名和包路径: taboolib.module.effect.ShowType
- 基本用途: 定义粒子特效显示的不同模式枚举
- 类型: 枚举(Enum)
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> NONE -> 无显示模式，特效不会自动显示
> ALWAYS_SHOW -> 始终显示模式，同步方式
> ALWAYS_SHOW_ASYNC -> 始终显示模式，异步方式
> ALWAYS_PLAY -> 始终播放模式，同步方式
> ALWAYS_PLAY_ASYNC -> 始终播放模式，异步方式

### 公开静态方法
> 无公开静态方法（仅包含枚举默认方法）

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 无额外类方法（仅包含枚举默认方法）

## 实现细节
- 这是一个简单的Java枚举类，定义了粒子特效系统中的五种显示模式
- 无参数构造函数，没有额外的字段或方法
- 用于在ParticleObj类中表示特效当前的显示状态

## 使用场景
> 标识粒子特效的当前运行模式
> 在ParticleObj中控制特效的显示方式
> 区分同步和异步运行的特效
> 区分普通显示和播放模式的特效

## 注意事项
> NONE表示特效没有自动显示，需要手动调用show方法
> ALWAYS_SHOW和ALWAYS_SHOW_ASYNC都是持续显示，但后者使用异步线程
> ALWAYS_PLAY和ALWAYS_PLAY_ASYNC用于实现了Playable接口的特效
> 异步模式可能提高性能，但要注意线程安全问题
