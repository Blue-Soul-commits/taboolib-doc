# NStar

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.NStar
- 基本用途: 用于创建和渲染N角星形粒子特效（N必须为奇数）
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> angle: double -> 角的角度，根据角数自动计算为360/corner
> corner: int -> 星形的角数，必须是奇数
> radius: double -> 星形的半径
> step: double -> 每个粒子之间的间隔（步长）

### 类方法
> NStar(Location origin, int corner, double radius, double step, ParticleSpawner spawner): NStar -> 创建N角星，如果corner不是奇数会抛出异常
> calculateLocations(): List<Location> -> 计算N角星上所有粒子位置
> show(): void -> 一次性显示整个N角星的所有粒子
> getAngle(): double -> 获取角度值
> setAngle(double angle): NStar -> 设置角度值并返回自身以支持链式调用
> getCorner(): int -> 获取角数
> setCorner(int corner): NStar -> 设置角数并返回自身以支持链式调用
> getRadius(): double -> 获取半径
> setRadius(double radius): NStar -> 设置半径并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): NStar -> 设置步长并返回自身以支持链式调用

## 实现细节
- 继承自抽象类ParticleObj，但未实现Playable接口，只支持静态显示
- 通过几何方法计算N角星的顶点和连线
- 算法基于固定半径和角度计算，先确定初始两点位置，然后通过向量旋转生成所有边
- N角星的角数必须是奇数，否则在构造时会抛出IllegalArgumentException异常
- 默认在xOz平面上生成星形，y坐标默认为0
- 可以通过矩阵变换来调整星形的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果
- 使用VectorUtils.rotateAroundAxisY方法实现向量的旋转

## 使用场景
> 创建星形粒子特效和装饰
> 用于魔法、召唤等游戏元素的视觉效果
> 标记特殊位置或区域
> 作为复杂粒子效果系统的组成部分
> 实现评分系统的视觉展示
> 作为奖励、成就或特殊状态的视觉提示

## 注意事项
> N角星的角数(corner)必须是奇数，否则会抛出异常
> 不支持动态播放(play)功能，因为未实现Playable接口
> 当半径过大或步长过小时，会生成大量粒子，可能影响服务器性能
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 尽管提供了setAngle方法，但通常不需要手动设置，角度会根据角数自动计算
> 星形的大小由radius参数控制，而不是由角数决定
