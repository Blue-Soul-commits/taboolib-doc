# Matrixs

## 基本信息
- 类名和包路径: taboolib.module.effect.math.Matrixs
- 基本用途: 提供与Matrix相关的静态实用方法，用于创建和操作各种类型的矩阵
- 类型: 工具类
- 所属模块: taboolib.module.effect.math

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> zeros(row: int, column: int): Matrix -> 返回一个指定行列数的全零矩阵
> ones(row: int, column: int): Matrix -> 返回一个指定行列数的全一矩阵
> eyes(row: int, column: int): Matrix -> 返回一个指定行列数的单位矩阵
> rotate2D(theta: double): Matrix -> 返回一个平面旋转矩阵
> rotateAroundXAxis(theta: double): Matrix -> 返回一个关于X轴的旋转矩阵
> rotateAroundYAxis(theta: double): Matrix -> 返回一个关于Y轴的旋转矩阵
> rotateAroundZAxis(theta: double): Matrix -> 返回一个关于Z轴的旋转矩阵
> scale(row: int, column: int, value: double): Matrix -> 返回一个放大或缩小的矩阵

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> 无实例方法

## 实现细节
- zeros方法返回一个所有元素都为0的矩阵
- ones方法返回一个所有元素都为1的矩阵
- eyes方法返回一个主对角线上元素为1，其他元素为0的矩阵
- rotate2D方法使用三角函数构造2D旋转矩阵
- rotateAroundXAxis、rotateAroundYAxis和rotateAroundZAxis方法返回3阶方阵，分别表示绕X轴、Y轴和Z轴的旋转变换
- scale方法将单位矩阵的每个元素乘以给定值，用于实现矩阵的缩放

## 使用场景
> 3D图形渲染中的坐标变换
> 粒子效果和视觉效果的几何变换
> 数学计算和矩阵运算
> 游戏中物体的旋转、缩放等变换操作

## 注意事项
> 旋转方法中的角度参数使用度数表示，内部会转换为弧度进行计算
> rotateAroundXAxis、rotateAroundYAxis和rotateAroundZAxis方法返回的都是3阶方阵
> 矩阵的行列从1开始索引，而不是从0开始
> 旋转矩阵使用的是左手坐标系，角度为负值时表示逆时针旋转

