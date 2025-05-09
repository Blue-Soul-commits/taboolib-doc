# PlayerFixedCoordinate

## 基本信息
- 类名和包路径: taboolib.module.effect.coordinate.PlayerFixedCoordinate
- 基本用途: 提供一个将X轴显示在玩家面前的坐标系，自动修正在XZ平面上的粒子朝向
- 类型: 工具类
- 所属模块: taboolib.module.effect.coordinate

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> originDot: Location -> 坐标系原点
> rotateAngle: double -> 旋转角度，与玩家朝向相关

### 类方法
> PlayerFixedCoordinate(playerLocation: Location) -> 构造函数，通过玩家位置创建一个固定坐标系
> getOriginDot(): Location -> 获取坐标系原点
> newLocation(x: double, y: double, z: double): Location -> 将给定的坐标转换为游戏世界中的实际位置

## 实现细节
- 构造函数接收玩家位置，记录玩家朝向的偏航角(yaw)作为旋转角度
- 原点设置在玩家当前位置，但仰俯角(pitch)被重置为0，确保坐标系平行于水平面
- newLocation方法使用了LocationUtils.rotateLocationAboutPoint来实现坐标转换
- 与PlayerBackCoordinate不同，原点直接位于玩家位置，而不是背后

## 使用场景
> 在玩家面前创建特效和粒子效果
> 实现玩家视野前方的UI元素
> 创建固定在玩家视角的3D效果
> 开发玩家交互式的全息显示

## 注意事项
> 坐标系原点位于玩家当前位置
> x轴正方向是玩家朝向的右手方向
> y轴正方向是向上的方向
> z轴正方向是玩家朝向的方向
> 坐标系会跟随玩家旋转，但不会受到玩家仰俯角(pitch)的影响
> 使用-x表示玩家左侧，这与寻常的坐标系有所不同
