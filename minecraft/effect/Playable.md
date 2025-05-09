# Playable

## 基本信息
- 类名和包路径: taboolib.module.effect.Playable
- 基本用途: 定义一个特效对象可播放的能力
- 类型: 接口(Interface)
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> play(): void -> 播放特效
> playNextPoint(): void -> 播放特效的下一个点

## 实现细节
- 这是一个简单的接口，用于标识特效对象是可播放的
- 定义了两个方法：play()和playNextPoint()
- play()方法用于播放整个特效
- playNextPoint()方法用于逐点播放特效，通常用于动画效果

## 使用场景
> 实现需要逐帧播放的粒子动画
> 创建具有时间线的特效序列
> 实现可交互的粒子效果
> 设计需要按特定顺序显示的复杂效果

## 注意事项
> 实现了此接口的特效对象可以使用ParticleObj中的alwaysPlay()和alwaysPlayAsync()方法
> playNextPoint()方法通常需要维护当前播放到的位置信息
> 接口由Zoyn创建，用于拓展ParticleObj的功能
> 未实现该接口的特效对象不能使用播放相关功能

