# SimpleAiExecutor

## 基本信息
- 类名和包路径: taboolib.module.ai.SimpleAiExecutor
- 基本用途: 提供实体 AI 操作的扩展函数集合
- 类型: Kotlin 文件（包含扩展函数）
- 所属模块: bukkit-nms-ai

## 类结构

### 公开静态字段
> pathfinderCreator: PathfinderCreator -> AI 路径创建器代理实例
> pathfinderExecutor: PathfinderExecutor -> AI 执行器代理实例

### 公开静态方法
> 无（文件中只包含扩展函数）

### 扩展函数
> LivingEntity.addGoalAi(ai: SimpleAi, priority: Int): Unit -> 注册一个 Goal AI
> LivingEntity.addTargetAi(ai: SimpleAi, priority: Int): Unit -> 注册一个 Target AI
> LivingEntity.replaceGoalAi(ai: SimpleAi, priority: Int): Unit -> 根据优先级替换 Goal AI
> LivingEntity.replaceTargetAi(ai: SimpleAi, priority: Int): Unit -> 根据优先级替换 Target AI
> LivingEntity.replaceGoalAi(ai: SimpleAi, priority: Int, name: String?): Unit -> 根据类名替换 Goal AI
> LivingEntity.replaceTargetAi(ai: SimpleAi, priority: Int, name: String?): Unit -> 根据类名替换 Target AI
> LivingEntity.removeGoalAi(priority: Int): Unit -> 根据优先级移除 Goal AI
> LivingEntity.removeTargetAi(priority: Int): Unit -> 根据优先级移除 Target AI
> LivingEntity.removeGoalAi(name: String): Unit -> 根据类名移除 Goal AI
> LivingEntity.removeTargetAi(name: String): Unit -> 根据类名移除 Target AI
> LivingEntity.clearGoalAi(): Unit -> 清空所有 Goal AI
> LivingEntity.clearTargetAi(): Unit -> 清空所有 Target AI
> LivingEntity.getGoalAi(): Iterable<*> -> 获取所有 Goal AI
> LivingEntity.getTargetAi(): Iterable<*> -> 获取所有 Target AI
> LivingEntity.setGoalAi(ai: Iterable<*>): Unit -> 设置所有 Goal AI
> LivingEntity.setTargetAi(ai: Iterable<*>): Unit -> 设置所有 Target AI
> LivingEntity.navigationMove(location: Location, speed: Double = 0.2): Boolean -> 移动实体到指定位置
> LivingEntity.navigationMove(target: LivingEntity, speed: Double = 0.2): Boolean -> 移动实体到目标实体
> LivingEntity.navigationReach(): Boolean -> 检查实体是否到达导航目标
> LivingEntity.controllerLookAt(target: Location): Unit -> 让实体看向指定位置
> LivingEntity.controllerLookAt(target: Entity): Unit -> 让实体看向指定实体
> LivingEntity.controllerJumpReady(): Unit -> 准备跳跃
> LivingEntity.controllerJumpCurrent(): Boolean -> 检查实体当前是否正在跳跃

## 实现细节
- 使用 nmsProxy 创建代理实例，根据 Minecraft 版本选择不同的实现类
- 所有扩展函数都是对 pathfinderExecutor 的方法调用的封装
- 支持 Universal（1.17+）和旧版本的 Minecraft

## 使用场景
> 管理实体的 AI 行为，如添加、替换、移除 AI
> 控制实体的移动、视线方向和跳跃行为
> 自定义实体的行为模式

## 注意事项
> Goal AI 和 Target AI 是两种不同类型的 AI，分别用于控制实体的行为和目标选择
> 优先级数值越小，AI 的优先级越高
> navigationMove 方法返回 Boolean 值表示导航是否成功开始

