# FilledCircle

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.FilledCircle
- 基本用途: 用于创建和渲染实心圆形的粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> radius: double -> 实心圆的半径
> sample: int -> 实心圆内要生成的粒子总数量
> currentCount: int -> 当前渲染到的粒子索引，用于连续播放特效

### 类方法
> FilledCircle(Location origin, double radius, int sample, ParticleSpawner spawner): FilledCircle -> 创建指定半径和粒子数量的实心圆
> calculateLocations(): List<Location> -> 计算实心圆内所有粒子位置
> show(): void -> 一次性显示整个实心圆的所有粒子
> calculateLocations(Location origin, long count): List<Location> -> 使用指定原点和粒子数量计算实心圆内所有粒子位置
> play(): void -> 以周期性方式播放实心圆特效，逐渐显示所有粒子
> playNextPoint(): void -> 显示实心圆中的下一个位置的粒子，由播放系统调用
> playWithTime(long time, long count): void -> 在指定时间内播放指定数量的粒子，均匀分布渲染

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用向日葵排列算法(Vogel's model)生成均匀分布的点阵，形成实心圆效果
- 粒子分布公式：r = radius * √(i/n)，θ = π * (1 + √5) * i
- 默认在xOz平面上生成圆，y坐标默认为0
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 额外提供了按时间控制渲染的方法(playWithTime)
- 可以通过矩阵变换来调整实心圆的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果

## 使用场景
> 创建实心圆形粒子特效和装饰
> 标记区域范围或技能影响区域
> 生成爆炸、冲击波等视觉效果
> 创建逐渐扩散或收缩的圆形粒子效果
> 作为复杂粒子效果系统的组成部分
> 模拟魔法阵、传送门等游戏元素

## 注意事项
> 粒子分布使用特殊算法，确保在实心圆内均匀分布
> sample参数决定了粒子的密度，数值越大效果越精细但也越消耗性能
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 播放模式下currentCount会持续增加，超过sample后会重置为0
> playWithTime方法提供了按时间均匀渲染的能力，适合创建逐渐形成的效果
> 与Circle类不同，FilledCircle渲染的是实心圆而不仅仅是圆周

