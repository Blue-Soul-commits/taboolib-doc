# Location
## 基本信息
- 类名和包路径: taboolib.common.util.Location
- 基本用途: 表示三维空间中的位置和方向
- 类型: 实用工具类
- 所属模块: common-util

## 类结构
### 公开静态方法
> locToBlock(loc: double): int -> 安全地将位置坐标（double）转换为方块坐标（int）
> normalizeYaw(yaw: float): float -> 将偏航角标准化为 +/-180 度范围内的值
> normalizePitch(pitch: float): float -> 将俯仰角标准化为 +/-90 度范围内的值

### 类内可被访问字段
> world: String -> 位置所在的世界名称
> x: double -> X 坐标
> y: double -> Y 坐标
> z: double -> Z 坐标
> pitch: float -> 俯仰角（垂直旋转）
> yaw: float -> 偏航角（水平旋转）

### 类方法
> Location(world: String, x: double, y: double, z: double) -> 使用给定坐标创建新位置
> Location(world: String, x: double, y: double, z: double, yaw: float, pitch: float) -> 使用给定坐标和方向创建新位置
> getWorld(): String -> 获取位置所在的世界名称
> setWorld(world: String): void -> 设置位置所在的世界名称
> getX(): double -> 获取 X 坐标
> setX(x: double): void -> 设置 X 坐标
> getBlockX(): int -> 获取 X 坐标的方块值
> getY(): double -> 获取 Y 坐标
> setY(y: double): void -> 设置 Y 坐标
> getBlockY(): int -> 获取 Y 坐标的方块值
> getZ(): double -> 获取 Z 坐标
> setZ(z: double): void -> 设置 Z 坐标
> getBlockZ(): int -> 获取 Z 坐标的方块值
> getYaw(): float -> 获取偏航角
> setYaw(yaw: float): void -> 设置偏航角
> getPitch(): float -> 获取俯仰角
> setPitch(pitch: float): void -> 设置俯仰角
> getDirection(): Vector -> 获取指向该位置面向方向的单位向量
> setDirection(vector: Vector): Location -> 设置位置的偏航角和俯仰角以指向给定向量的方向
> add(vec: Location): Location -> 将位置与另一个位置相加
> add(vec: Vector): Location -> 将位置与向量相加
> add(x: double, y: double, z: double): Location -> 将位置与给定坐标相加
> subtract(vec: Location): Location -> 从位置中减去另一个位置
> subtract(vec: Vector): Location -> 从位置中减去向量
> subtract(x: double, y: double, z: double): Location -> 从位置中减去给定坐标
> length(): double -> 获取位置的大小（到原点的距离）
> lengthSquared(): double -> 获取位置大小的平方
> distance(o: Location): double -> 获取此位置与另一个位置之间的距离
> distanceSquared(o: Location): double -> 获取此位置与另一个位置之间距离的平方
> multiply(m: double): Location -> 执行标量乘法，将所有分量乘以标量
> zero(): Location -> 将此位置的分量归零
> equals(o: Object): boolean -> 判断此位置是否与另一个对象相等
> hashCode(): int -> 获取此位置的哈希码
> toString(): String -> 获取此位置的字符串表示
> toVector(): Vector -> 基于此位置构造新的向量
> clone(): Location -> 克隆此位置
> checkFinite(): void -> 检查此位置的每个分量是否有限
> referTo(yaw: float, offset: float, multiply: double, height: double): Location -> 基于源位置创建参照坐标

## 实现细节
- 位置由世界名称、三维坐标（x、y、z）和方向（偏航角、俯仰角）组成
- 提供了丰富的位置操作方法，包括加法、减法、乘法等
- 支持位置之间的距离计算
- 支持位置与向量之间的转换
- 实现了 Cloneable 接口，支持位置的克隆
- 提供了角度标准化方法，确保角度在有效范围内

## 使用场景
> 在游戏或模拟环境中表示实体的位置和方向
> 进行空间计算，如距离测量、方向确定等
> 在三维空间中进行位置变换和操作
> 用于表示方块在世界中的位置

## 注意事项
> 角度值以度为单位，而非弧度
> 距离计算方法使用了开销较大的平方根函数，不建议频繁调用
> 在不同世界之间的位置操作（如加法、距离计算）会抛出异常
> 位置操作方法（如 add、subtract、multiply）会修改当前位置对象，而不是创建新对象
