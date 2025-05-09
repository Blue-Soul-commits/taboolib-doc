# Astroid

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.Astroid
- 基本用途: 用于创建和渲染星形线(星状四瓣曲线)粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> radius: double -> 星形线的半径参数
> step: double -> 角度步进值，控制粒子密度
> currentT: double -> 当前渲染到的角度参数，用于连续播放特效

### 类方法
> Astroid(Location origin, ParticleSpawner spawner): Astroid -> 创建默认半径为1的星形线
> Astroid(double radius, Location origin, ParticleSpawner spawner): Astroid -> 创建指定半径的星形线
> getRadius(): double -> 获取星形线的半径
> setRadius(double radius): void -> 设置星形线的半径
> getStep(): double -> 获取角度步进值
> setStep(double step): void -> 设置角度步进值
> calculateLocations(): List<Location> -> 计算星形线上所有粒子位置
> show(): void -> 一次性显示整个星形线的所有粒子
> play(): void -> 以周期性方式播放星形线特效，从起始点开始逐渐显示
> playNextPoint(): void -> 显示星形线上的下一个位置的粒子，由播放系统调用

## 实现细节
- 继承自抽象类ParticleObj，实现了Playable接口
- 使用星形线的参数方程：x = (r·cos(t))³，z = (r·sin(t))³
- 星形线默认在xOz平面上生成，y坐标默认为0
- 渲染时遍历从0到360度的所有角度，以step为步长
- 支持三种渲染模式：一次性显示、连续播放、单步播放
- 可以通过矩阵变换来调整星形线的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 默认使用1度的步长进行显示，可通过setStep方法调整粒子密度

## 使用场景
> 创建星形粒子特效和装饰
> 生成四瓣星状几何图案
> 用于技能释放或法术施展的视觉效果
> 作为复杂粒子效果系统的组成部分
> 实现特殊的几何图形粒子效果

## 注意事项
> 星形线是一种特殊的代数曲线，生成的图形是四瓣星状图案
> 角度使用的是度数而非弧度，计算时会自动转换
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 当步长过小时，会生成大量粒子，可能影响服务器性能
> 播放模式下currentT会持续增加，超过360度后会重置为0
> show()方法默认使用1度的步长，而calculateLocations()使用设置的step值
