# Circle

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Circle
- 基本用途: 用于创建和渲染完整圆形粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 继承自Arc类的字段，无自定义字段

### 类方法
> Circle(Location origin, ParticleSpawner spawner): Circle -> 创建默认半径为1的圆
> Circle(Location origin, double radius, ParticleSpawner spawner): Circle -> 创建指定半径、默认步长为1的圆
> Circle(Location origin, double radius, double step, ParticleSpawner spawner): Circle -> 创建指定半径和步长的圆，默认周期为20tick
> Circle(Location origin, double radius, double step, long period, ParticleSpawner spawner): Circle -> 创建完全自定义参数的圆
> 继承自Arc类的所有方法

## 实现细节
- 继承自Arc类，本质上是一个角度为360度的弧
- 通过Arc类的构造方法创建，将角度参数固定为360度
- 默认在xOz平面上生成圆，y坐标默认为0
- 支持Arc类的所有渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整圆的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 通过继承Arc类，重用了角度计算的逻辑，使代码更简洁

## 使用场景
> 创建圆形粒子特效和装饰
> 标记区域范围或技能影响范围
> 作为导航或指引的视觉提示
> 实现环形粒子阵列或光环效果
> 作为复杂粒子效果系统的基础组件
> 创建动态的环绕效果

## 注意事项
> 作为Arc的子类，继承了Arc的所有特性和使用注意事项
> 当半径过大或步长过小时，会生成大量粒子，可能影响服务器性能
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 播放模式下会从0度开始逐渐显示到360度，形成动态生成圆的效果
> 虽然类结构简单，但提供了丰富的功能，因为继承了Arc类的所有方法
