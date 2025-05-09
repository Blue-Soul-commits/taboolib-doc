# Sphere

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Sphere
- 基本用途: 用于创建和渲染球体粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> phi: double -> 黄金角度常量，约等于137.5度(π(3-√5))，用于均匀分布点
> locations: List<Location> -> 缓存球体表面所有点的位置
> sample: int -> 样本点个数，即粒子的数量
> radius: double -> 球体的半径

### 类方法
> Sphere(Location origin, ParticleSpawner spawner): Sphere -> 创建默认参数(样本点50，半径1)的球体
> Sphere(Location origin, int sample, double radius, ParticleSpawner spawner): Sphere -> 创建指定样本点数量和半径的球体
> calculateLocations(): List<Location> -> 计算球体表面所有粒子位置
> show(): void -> 一次性显示整个球体的所有粒子
> getSample(): int -> 获取样本点数量
> setSample(int sample): Sphere -> 设置样本点数量并返回自身以支持链式调用
> getRadius(): double -> 获取球体半径
> setRadius(double radius): Sphere -> 设置球体半径并返回自身以支持链式调用
> resetLocations(): void -> 重新计算并缓存球体表面所有点的位置

## 实现细节
- 继承自抽象类ParticleObj，但未实现Playable接口，只支持静态显示
- 使用基于黄金螺旋算法(Fibonacci sphere algorithm)的方法在球体表面均匀分布点
- 算法来源于Stack Overflow的一个回答，链接在类注释中提供
- 通过数学公式将球坐标转换为笛卡尔坐标系：
  - y从1到-1均匀分布
  - yRadius = √(1-y²)计算当前y位置处的半径
  - x = cos(θ) * radius * yRadius
  - z = sin(θ) * radius * yRadius
  - y *= radius
- 在构造时预计算并缓存所有点位，提高渲染效率
- 可以通过矩阵变换来调整球体的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果

## 使用场景
> 创建球体粒子特效和装饰
> 标记区域范围或技能影响范围
> 模拟法术、护盾、能量场等游戏元素
> 作为星球、气泡等视觉元素
> 实现爆炸、冲击波等特效
> 作为复杂粒子效果系统的组成部分

## 注意事项
> 不支持动态播放(play)功能，因为未实现Playable接口
> sample参数决定了粒子的密度，数值越大效果越精细但也越消耗性能
> 球体表面的粒子分布是均匀的，这得益于黄金螺旋算法
> 修改sample或radius参数后会自动调用resetLocations方法重新计算点位
> 默认参数创建的球体有50个粒子点，对于大型球体可能需要更多的样本点
> 与FilledCircle不同，Sphere只渲染球体表面，不会填充内部
