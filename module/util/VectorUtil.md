# VectorUtil

## 基本信息
- 类名和包路径: taboolib.module.ui.VectorUtil
- 基本用途: 提供向量相关的实用工具，用于处理物品投掷、实体推动等物理效果
- 类型: 工具类
- 所属模块: taboolib.module.ui

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> itemDrop(player: Player, itemStack: ItemStack): Item -> 使用默认参数从玩家位置投掷物品
> itemDrop(player: Player, itemStack: ItemStack, bulletSpread: double, radius: double): Item -> 从玩家位置投掷物品，可自定义散布范围和速度
> entityPush(entity: Entity, to: Location, velocity: double): void -> 将实体推向指定位置，使用物理计算确定抛物线

### 类内可被访问字段
> 无

### 类方法
> calculateHangTime(launchAngle: double, v: double, elev: double, g: double): double -> 计算实体在空中停留的时间
> normalizeVector(victor: Vector): Vector -> 标准化向量，使其长度为1
> calculateLaunchAngle(from: Location, to: Location, v: double, elevation: double, g: double): Double -> 计算从起点到终点的发射角度

## 实现细节
- itemDrop 方法使用玩家的视角方向作为物品投掷的基础方向
- 支持添加随机散布效果，使物品投掷更加自然
- entityPush 方法使用物理公式计算抛物线，使实体移动更加真实
- 内部使用多个辅助方法进行物理计算，包括发射角度、悬停时间和向量标准化
- 使用随机数添加微小的噪声，使运动更加自然

## 使用场景
> 创建自定义物品投掷效果，如从玩家视角方向投掷物品
> 实现实体的物理推动，如将怪物推向特定位置
> 需要精确控制物品或实体运动轨迹的插件功能

## 注意事项
> itemDrop 方法会在玩家头部位置(+1.5高度)生成掉落物，而不是从玩家手中
> entityPush 方法在目标距离为0时不会产生效果
> 物理计算使用了重力常数20.0D，这是Minecraft中的近似值
> 随机数生成使用了多个新的Random实例，可能影响性能
