# Matrix

## 基本信息
- 类名和包路径: taboolib.module.effect.math.Matrix
- 基本用途: 实现矩阵运算和矩阵变换功能
- 类型: 实体类
- 所属模块: taboolib.module.effect.math

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> createVector(start: Location, end: Location): Vector -> 通过两点创建向量

### 类内可被访问字段
> m: double[][] -> 存储矩阵数据的二维数组

### 类方法
> Matrix(row: int, column: int) -> 构造一个指定行列数的零矩阵
> Matrix(m: double[][]) -> 通过二维数组构造矩阵
> Matrix(matrix: Matrix) -> 通过已有矩阵构造新矩阵（复制构造）
> getRow(): int -> 获取矩阵的行数
> getColumn(): int -> 获取矩阵的列数
> getAsArray(): double[][] -> 获取矩阵的二维数组表示
> get(row: int, column: int): double -> 获取矩阵指定位置的值
> set(row: int, column: int, value: double): Matrix -> 设置矩阵指定位置的值
> fill(row: int, value: double): Matrix -> 用同一实数填充矩阵的某一行
> getRowAsArray(row: int): double[] -> 获取矩阵的某一行为数组
> getColumnAsArray(column: int): double[] -> 获取矩阵的某一列为数组
> isSameRow(matrix: Matrix): boolean -> 判断两个矩阵行数是否相同
> isSameColumn(matrix: Matrix): boolean -> 判断两个矩阵列数是否相同
> isSameRowAndColumn(matrix: Matrix): boolean -> 判断两个矩阵行列数是否都相同
> invert(): Matrix -> 矩阵转置
> plus(matrix: Matrix): Matrix -> 矩阵加法
> multiply(value: double): Matrix -> 矩阵数乘
> multiply(matrix: Matrix): Matrix -> 矩阵乘法
> prettyPrinting(): void -> 将矩阵以美观方式打印出来
> applyLocation(location: Location, origin: Location): Location -> 将矩阵变换应用到坐标上
> applyVector(vector: Vector): Vector -> 将矩阵变换应用到向量上
> applyIn2DVector(vector: Vector): Vector -> 内部方法，将2x2矩阵应用到向量上
> applyIn3DVector(vector: Vector): Vector -> 内部方法，将3x3矩阵应用到向量上

## 实现细节
- 矩阵使用二维数组表示，支持基本的矩阵运算
- 矩阵索引从1开始，而不是从0开始，即get(1,1)表示获取第一行第一列的元素
- 所有的乘法操作都是左乘，即A.multiply(B)表示A×B
- 矩阵转置使用invert()方法，会返回一个新的矩阵
- 矩阵应用于向量时，会根据矩阵维度自动选择2D或3D应用方式
- 类支持链式调用，很多方法返回的是this引用

## 使用场景
> 进行坐标变换和3D图形变换
> 实现旋转、缩放、平移等几何变换
> 粒子效果中的数学计算
> 复杂的线性代数计算

## 注意事项
> 矩阵索引从1开始，不是从0开始，这点与Java数组习惯不同
> 只能应用2x2和3x3的方阵进行向量变换
> 矩阵乘法要求左矩阵的列数等于右矩阵的行数
> plus方法要求两矩阵大小相同
> applyVector方法只适用于2x2或3x3的方阵，其他尺寸会抛出异常
