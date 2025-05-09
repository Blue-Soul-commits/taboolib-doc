# LocationUtils

## 基本信息
- 类名和包路径: taboolib.module.effect.utils.LocationUtils
- 基本用途: 提供坐标相关的工具方法，主要用于计算和处理坐标点的旋转
- 类型: 工具类
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> rotateLocationAboutPoint(location: Location, angle: double, point: Location): Location -> 在二维平面上利用给定的中心点逆时针旋转一个点
> rotateLocationAboutVector(location: Location, origin: Location, angle: double, axis: Vector): Location -> 将一个点围绕另一个向量旋转

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 无实例方法

## 实现细节
- rotateLocationAboutPoint方法使用三角函数计算二维平面上的点绕中心点旋转后的新坐标
- rotateLocationAboutVector方法利用VectorUtils.rotateAroundAxis实现点绕向量轴的旋转
- 所有方法都返回新的Location对象，不会修改原始对象

## 使用场景
> 游戏中实现特效旋转动画，如粒子效果围绕玩家旋转
> 创建几何形状时，通过旋转计算各个点的位置
> 3D空间中物体或实体的旋转变换

## 注意事项
> 方法返回的是新的Location对象，原始Location不会被修改
> rotateLocationAboutPoint方法只在水平面(X-Z平面)进行旋转，Y坐标保持不变
> 角度参数使用度数表示，内部会转换为弧度进行计算
