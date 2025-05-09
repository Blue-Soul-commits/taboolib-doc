# OctagonalStar

## 基本信息
- 类名和包路径: taboolib.module.effect.shape.OctagonalStar
- 基本用途: 用于创建和渲染八角星形粒子特效
- 类型: 粒子特效形状类
- 所属模块: taboolib.module.effect.shape

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> radius: double -> 八角星的半径
> step: double -> 每个粒子之间的间隔（步长）

### 类方法
> OctagonalStar(Location origin, double radius, double step, ParticleSpawner spawner): OctagonalStar -> 创建指定半径和步长的八角星
> calculateLocations(): List<Location> -> 计算八角星上所有粒子位置
> show(): void -> 一次性显示整个八角星的所有粒子
> getRadius(): double -> 获取半径
> setRadius(double radius): OctagonalStar -> 设置半径并返回自身以支持链式调用
> getStep(): double -> 获取步长
> setStep(double step): OctagonalStar -> 设置步长并返回自身以支持链式调用

## 实现细节
- 继承自抽象类ParticleObj，但未实现Playable接口，只支持静态显示
- 通过几何方法计算八角星的顶点和连线
- 算法使用固定角度(45度)计算八角星的各个顶点，并连接对角点形成星形
- 八角星的角度固定为45度，无法像NStar类那样自定义角数
- 默认在xOz平面上生成八角星，y坐标默认为0
- 通过向量旋转(VectorUtils.rotateAroundAxisY)实现八个相同边的生成
- 可以通过矩阵变换来调整八角星的位置和形状
- 每次渲染时，通过ParticleSpawner接口生成实际的粒子效果

## 使用场景
> 创建八角星形粒子特效和装饰
> 用于魔法、召唤等游戏元素的视觉效果
> 作为特殊标记或符号的可视化表示
> 用于东方风格场景的装饰元素
> 作为复杂粒子效果系统的组成部分
> 实现特定主题的视觉效果

## 注意事项
> 不支持动态播放(play)功能，因为未实现Playable接口
> 八角星形状固定，无法像NStar类那样自定义角数
> 当半径过大或步长过小时，会生成大量粒子，可能影响服务器性能
> 默认在xOz平面上生成，如需在其他平面生成需使用矩阵变换
> 相比NStar类，该类专门针对八角星进行了优化，实现逻辑较为简化
> 若需要创建其他角数的星形，应使用NStar类而非此类
