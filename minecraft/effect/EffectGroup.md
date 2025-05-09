# EffectGroup

## 基本信息
- 类名和包路径: taboolib.module.effect.EffectGroup
- 基本用途: 管理和操作一组粒子特效对象，提供批量控制和变换功能
- 类型: 实体类
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> effectList: List<ParticleObj> -> 特效对象列表

### 类方法
> EffectGroup() -> 默认构造函数，创建空特效组
> EffectGroup(effectList: List<ParticleObj>) -> 通过特效列表构造特效组
> addEffect(particleObj: ParticleObj): EffectGroup -> 添加单个特效对象
> addEffect(particleObj: ParticleObj...): EffectGroup -> 添加多个特效对象
> calculateLocations(): List<Location> -> 计算所有特效的位置列表
> removeEffect(index: int): EffectGroup -> 移除指定索引的特效
> setPeriod(period: long): EffectGroup -> 设置所有特效的循环周期
> scale(value: double): EffectGroup -> 缩放所有特效
> rotateAroundXAxis(angle: double): EffectGroup -> 绕X轴旋转所有特效
> rotateAroundYAxis(angle: double): EffectGroup -> 绕Y轴旋转所有特效
> rotateAroundZAxis(angle: double): EffectGroup -> 绕Z轴旋转所有特效
> addMatrix(matrix: Matrix): EffectGroup -> 为所有特效添加变换矩阵
> removeMatrix(): EffectGroup -> 移除所有特效的变换矩阵
> show(): EffectGroup -> 一次性显示所有特效
> alwaysShow(): EffectGroup -> 持续显示所有特效（同步）
> alwaysShowAsync(): EffectGroup -> 持续显示所有特效（异步）
> play(): EffectGroup -> 一次性播放所有可播放的特效
> alwaysPlay(): EffectGroup -> 持续播放所有可播放的特效（同步）
> alwaysPlayAsync(): EffectGroup -> 持续播放所有可播放的特效（异步）
> getEffectList(): List<ParticleObj> -> 获取特效列表

## 实现细节
- 特效组通过ArrayList存储和管理多个ParticleObj对象
- 提供链式调用方法，所有操作方法都返回this
- 支持批量添加和移除特效对象
- 提供多种几何变换方法：缩放和三轴旋转
- 使用Matrixs工具类创建变换矩阵
- 对可播放特效(实现Playable接口)提供特殊的播放功能
- calculateLocations方法使用Java 8 Stream API整合所有特效的位置

## 使用场景
> 管理和控制多个相关联的粒子特效
> 创建复杂的组合特效
> 对多个特效同时应用几何变换
> 实现特效的同步显示和播放
> 创建可重用的特效组合

## 注意事项
> 不建议将2D特效和3D特效放在同一组，可能导致变换效果不一致
> 默认使用3x3矩阵进行变换
> 播放方法(play, alwaysPlay, alwaysPlayAsync)只对实现了Playable接口的特效有效
> 使用异步方法时要注意线程安全问题
> calculateLocations方法会计算所有特效的位置，可能较为耗时
