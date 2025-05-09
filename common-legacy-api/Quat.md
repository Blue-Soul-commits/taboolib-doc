# Quat

## 基本信息
- 类名和包路径: taboolib.common5.Quat
- 基本用途: 提供四元数（Quaternion）数学运算，用于 3D 空间中的旋转和位置表示
- 类型: 不可变类
- 所属模块: common-legacy-api

## 类结构

### 公开静态字段
> DBL_EPSILON: double -> 双精度浮点数的极小值常量，用于浮点数比较

### 公开静态方法
> one(): Quat -> 返回一个所有分量都为 1 的四元数 (1,1,1,0)
> zero(): Quat -> 返回一个所有分量都为 0 的四元数 (0,0,0,0)
> at(x: double, y: double, z: double): Quat -> 创建一个 w 分量为 0 的四元数
> at(x: double, y: double, z: double, w: double): Quat -> 创建一个指定所有分量的四元数
> radiansAxis(angle: double, vector: Quat): Quat -> 创建一个表示绕指定向量旋转指定弧度的四元数
> radiansAxis(angle: double, x: double, y: double, z: double): Quat -> 创建一个表示绕指定轴旋转指定弧度的四元数

### 类内可被访问字段
> x: double -> 四元数的 x 分量
> y: double -> 四元数的 y 分量
> z: double -> 四元数的 z 分量
> w: double -> 四元数的 w 分量

### 类方法
> Quat(x: double, y: double, z: double, w: double): constructor -> 创建一个四元数实例
> x(): double -> 获取 x 分量
> y(): double -> 获取 y 分量
> z(): double -> 获取 z 分量
> w(): double -> 获取 w 分量
> length(): double -> 计算四元数的长度（模）
> lengthSquared(): double -> 计算四元数长度的平方
> rotate(vector: Quat): Quat -> 使用当前四元数旋转指定向量
> rotate(x: double, y: double, z: double): Quat -> 使用当前四元数旋转指定坐标
> rotate2D(angle: double, aboutX: double, aboutZ: double): Quat -> 在 XZ 平面上绕指定点旋转
> rotate2D(angle: double, aboutX: double, aboutZ: double, translateX: double, translateZ: double): Quat -> 在 XZ 平面上绕指定点旋转并平移
> getMinimum(v2: Quat): Quat -> 返回当前四元数与另一个四元数各分量的最小值组成的新四元数
> getMaximum(v2: Quat): Quat -> 返回当前四元数与另一个四元数各分量的最大值组成的新四元数
> equals(o: Object): boolean -> 判断两个四元数是否相等
> hashCode(): int -> 获取四元数的哈希码
> toString(): String -> 获取四元数的字符串表示

## 实现细节
- 四元数是不可变的，所有操作都会返回新的四元数实例
- 使用标准的四元数数学公式实现旋转操作
- 提供了 2D 旋转方法，简化在 XZ 平面上的旋转操作
- 实现了标准的 equals、hashCode 和 toString 方法
- 提供了常用的工厂方法如 one()、zero() 和 at() 简化四元数创建

## 使用场景
> 3D 游戏中的物体旋转和方向表示
> 相机视角控制和平滑过渡
> 物理引擎中的刚体旋转计算
> 粒子效果和动画系统中的旋转插值

## 注意事项
> 四元数长度为零时，rotate 方法会抛出 ArithmeticException 异常
> 角度参数通常以度为单位，内部会自动转换为弧度
> 在 rotate2D 方法中，旋转是在 XZ 平面上进行的，Y 轴值保持不变
> 四元数比欧拉角更适合表示连续旋转，可以避免万向节锁问题