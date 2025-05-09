# Vector
## 基本信息
- 类名和包路径: taboolib.common.util.Vector
- 基本用途: 表示三维空间中的向量，提供向量运算功能
- 类型: 实用工具类
- 所属模块: common-util

## 类结构
### 公开静态方法
> getEpsilon(): double -> 获取用于equals()的阈值
> getMinimum(v1: Vector, v2: Vector): Vector -> 获取两个向量的最小分量
> getMaximum(v1: Vector, v2: Vector): Vector -> 获取两个向量的最大分量
> getRandom(): Vector -> 获取随机向量，分量在0到1之间
> square(num: double): double -> 计算平方值
> floor(num: double): int -> 向下取整
> isFinite(d: double): boolean -> 检查double值是否有限
> isFinite(f: float): boolean -> 检查float值是否有限
> constrainToRange(value: double, min: double, max: double): double -> 将值限制在指定范围内
> checkFinite(d: double, message: String): void -> 检查值是否有限，否则抛出异常
> checkFinite(f: float, message: String): void -> 检查值是否有限，否则抛出异常

### 类内可被访问字段
> x: double -> X分量
> y: double -> Y分量
> z: double -> Z分量

### 类方法
> Vector() -> 构造所有分量为0的向量
> Vector(x: int, y: int, z: int) -> 使用整数分量构造向量
> Vector(x: double, y: double, z: double) -> 使用双精度分量构造向量
> Vector(x: float, y: float, z: float) -> 使用单精度分量构造向量
> add(vec: Vector): Vector -> 向量加法
> subtract(vec: Vector): Vector -> 向量减法
> multiply(vec: Vector): Vector -> 向量乘法
> divide(vec: Vector): Vector -> 向量除法
> copy(vec: Vector): Vector -> 复制另一个向量
> length(): double -> 获取向量长度
> lengthSquared(): double -> 获取向量长度的平方
> distance(o: Vector): double -> 计算与另一个向量的距离
> distanceSquared(o: Vector): double -> 计算与另一个向量的距离平方
> angle(other: Vector): float -> 计算与另一个向量的夹角（弧度）
> midpoint(other: Vector): Vector -> 设置为与另一个向量的中点
> getMidpoint(other: Vector): Vector -> 获取与另一个向量的中点
> multiply(m: int): Vector -> 标量乘法（整数）
> multiply(m: double): Vector -> 标量乘法（双精度）
> multiply(m: float): Vector -> 标量乘法（单精度）
> dot(other: Vector): double -> 计算点积
> crossProduct(o: Vector): Vector -> 计算叉积
> getCrossProduct(o: Vector): Vector -> 获取叉积（不修改原向量）
> normalize(): Vector -> 归一化向量
> zero(): Vector -> 将向量归零
> normalizeZeros(): Vector -> 将-0.0转换为0.0
> isInAABB(min: Vector, max: Vector): boolean -> 检查向量是否在轴对齐包围盒内
> isInSphere(origin: Vector, radius: double): boolean -> 检查向量是否在球体内
> isNormalized(): boolean -> 检查向量是否已归一化
> rotateAroundX(angle: double): Vector -> 绕X轴旋转
> rotateAroundY(angle: double): Vector -> 绕Y轴旋转
> rotateAroundZ(angle: double): Vector -> 绕Z轴旋转
> rotateAroundAxis(axis: Vector, angle: double): Vector -> 绕任意轴旋转
> rotateAroundNonUnitAxis(axis: Vector, angle: double): Vector -> 绕非单位轴旋转
> getX(): double -> 获取X分量
> getBlockX(): int -> 获取X分量的方块值
> getY(): double -> 获取Y分量
> getBlockY(): int -> 获取Y分量的方块值
> getZ(): double -> 获取Z分量
> getBlockZ(): int -> 获取Z分量的方块值
> setX(x: int): Vector -> 设置X分量（整数）
> setX(x: double): Vector -> 设置X分量（双精度）
> setX(x: float): Vector -> 设置X分量（单精度）
> setY(y: int): Vector -> 设置Y分量（整数）
> setY(y: double): Vector -> 设置Y分量（双精度）
> setY(y: float): Vector -> 设置Y分量（单精度）
> setZ(z: int): Vector -> 设置Z分量（整数）
> setZ(z: double): Vector -> 设置Z分量（双精度）
> setZ(z: float): Vector -> 设置Z分量（单精度）
> equals(obj: Object): boolean -> 检查是否与另一个对象相等
> hashCode(): int -> 获取哈希码
> clone(): Vector -> 克隆向量
> toString(): String -> 获取字符串表示
> toLocation(world: String): Location -> 转换为位置（偏航和俯仰为0）
> toLocation(world: String, yaw: float, pitch: float): Location -> 转换为位置
> checkFinite(): void -> 检查所有分量是否有限

## 实现细节
- 向量由三个双精度浮点数表示（x、y、z）
- 大多数操作方法会修改向量本身并返回自身引用，便于链式调用
- 提供了非修改性的替代方法（如getMidpoint、getCrossProduct）
- 使用epsilon值（0.000001）进行浮点数比较，以处理浮点误差
- 实现了Cloneable和Serializable接口，支持克隆和序列化

## 使用场景
> 表示三维空间中的位置、方向或速度
> 进行物理模拟和碰撞检测
> 计算几何问题，如距离、角度、投影等
> 图形渲染和动画中的变换操作

## 注意事项
> 大多数操作会修改向量本身，如需保留原始值，应先克隆
> 长度计算使用开销较大的平方根函数，不建议频繁调用
> 旋转操作使用弧度而非角度
> 向量归一化前应确保长度不为零，否则会导致除零错误