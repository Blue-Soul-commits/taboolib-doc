# PlayerFrontCoordinate

## 基本信息
- 类名和包路径: taboolib.module.effect.coordinate.PlayerFrontCoordinate
- 基本用途: 提供一个玩家面前的坐标系，将玩家面前作为一个新坐标系
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
> PlayerFrontCoordinate(playerLocation: Location) -> 构造函数，通过玩家位置创建一个前方坐标系
> getOriginDot(): Location -> 获取坐标系原点
> newLocation(x: double, y: double, z: double): Location -> 将给定的坐标转换为游戏世界中的实际位置

## 实现细节
- 构造函数接收玩家位置，记录玩家朝向的偏航角(yaw)加上90度作为旋转角度
- 原点设置在玩家当前位置，但仰俯角(pitch)被重置为0，确保坐标系平行于水平面
- newLocation方法使用了LocationUtils.rotateLocationAboutPoint来实现坐标转换
- 与其他坐标系不同，这里的坐标映射关系是：游戏世界(y,z,x)对应坐标系(x,y,z)

## 使用场景
> 在玩家面前创建特效和粒子效果
> 实现玩家视野前方的UI元素或信息展示
> 创建跟随玩家朝向的视觉效果
> 开发需要与玩家面向方向一致的功能

## 注意事项
> 坐标系原点位于玩家当前位置
> 坐标映射关系：坐标系的x轴对应游戏世界的y轴，坐标系的y轴对应游戏世界的z轴，坐标系的z轴对应游戏世界的x轴
> 坐标系不受玩家仰俯角(pitch)的影响，始终平行于水平面
> 旋转角度是玩家的偏航角(yaw)加上90度，这与PlayerFixedCoordinate有所不同
> 坐标添加顺序为(y, z, x)，而不是常见的(x, y, z)，使用时需特别注意
