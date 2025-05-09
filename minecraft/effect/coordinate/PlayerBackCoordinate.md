# PlayerBackCoordinate

## 基本信息
- 类名和包路径: taboolib.module.effect.coordinate.PlayerBackCoordinate
- 基本用途: 提供一个玩家后背的直角坐标系，用于在玩家背后创建各种效果
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
> PlayerBackCoordinate(playerLocation: Location) -> 构造函数，通过玩家位置创建一个后背坐标系
> newLocation(x: double, y: double, z: double): Location -> 将给定的坐标转换为游戏世界中的实际位置

## 实现细节
- 构造函数接收玩家位置，记录玩家朝向的偏航角(yaw)作为旋转角度
- 原点设置在玩家背后一小段距离处(0.3格)，通过玩家方向向量的反方向获得
- 坐标系中的仰俯角(pitch)被重置为0，确保坐标系平行于水平面
- newLocation方法使用了LocationUtils.rotateLocationAboutPoint来实现坐标转换

## 使用场景
> 在玩家背后创建特效和粒子效果
> 实现跟随玩家的背部装饰
> 为玩家添加翅膀、披风等视觉效果
> 创建跟随玩家的宠物或伙伴效果

## 注意事项
> 坐标系原点位于玩家背后0.3格处
> x轴正方向是玩家背后向左的方向
> y轴正方向是向上的方向
> z轴正方向是玩家正面方向
> 当玩家旋转时，该坐标系会跟随玩家旋转
