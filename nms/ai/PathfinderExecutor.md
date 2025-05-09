# PathfinderExecutor

## 基本信息
- 类名和包路径: taboolib.module.ai.PathfinderExecutor
- 基本用途: 提供Minecraft实体AI行为控制的抽象基类
- 类型: 抽象类
- 所属模块: bukkit-nms-ai

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 抽象方法
> getEntityInsentient(LivingEntity entity): Object -> 获取实体的NMS EntityInsentient对象
> getNavigation(LivingEntity entity): Object -> 获取实体的导航控制器
> getControllerJump(LivingEntity entity): Object -> 获取实体的跳跃控制器
> getControllerMove(LivingEntity entity): Object -> 获取实体的移动控制器
> getControllerLook(LivingEntity entity): Object -> 获取实体的视线控制器
> getGoalSelector(LivingEntity entity): Object -> 获取实体的目标选择器
> getTargetSelector(LivingEntity entity): Object -> 获取实体的目标选择器
> getPathEntity(LivingEntity entity): Object -> 获取实体的路径实体
> setPathEntity(LivingEntity entity, Object pathEntity): void -> 设置实体的路径实体
> addGoalAi(LivingEntity entity, SimpleAi ai, int priority): void -> 添加目标AI
> addTargetAi(LivingEntity entity, SimpleAi ai, int priority): void -> 添加目标选择AI
> replaceGoalAi(LivingEntity entity, SimpleAi ai, int priority): void -> 替换目标AI
> replaceTargetAi(LivingEntity entity, SimpleAi ai, int priority): void -> 替换目标选择AI
> replaceGoalAi(LivingEntity entity, SimpleAi ai, int priority, @Nullable String name): void -> 根据名称替换目标AI
> replaceTargetAi(LivingEntity entity, SimpleAi ai, int priority, @Nullable String name): void -> 根据名称替换目标选择AI
> removeGoalAi(LivingEntity entity, int priority): void -> 根据优先级移除目标AI
> removeTargetAi(LivingEntity entity, int priority): void -> 根据优先级移除目标选择AI
> removeGoalAi(LivingEntity entity, String name): void -> 根据名称移除目标AI
> removeTargetAi(LivingEntity entity, String name): void -> 根据名称移除目标选择AI
> clearGoalAi(LivingEntity entity): void -> 清除所有目标AI
> clearTargetAi(LivingEntity entity): void -> 清除所有目标选择AI
> getGoalAi(LivingEntity entity): Iterable -> 获取所有目标AI
> getTargetAi(LivingEntity entity): Iterable -> 获取所有目标选择AI
> setGoalAi(LivingEntity entity, Iterable ai): void -> 设置所有目标AI
> setTargetAi(LivingEntity entity, Iterable ai): void -> 设置所有目标选择AI
> navigationMove(LivingEntity entity, Location location): boolean -> 移动实体到指定位置
> navigationMove(LivingEntity entity, Location location, double speed): boolean -> 以指定速度移动实体到指定位置
> navigationMove(LivingEntity entity, LivingEntity target): boolean -> 移动实体到目标实体
> navigationMove(LivingEntity entity, LivingEntity target, double speed): boolean -> 以指定速度移动实体到目标实体
> navigationReach(LivingEntity entity): boolean -> 检查实体是否到达目标位置
> controllerLookAt(LivingEntity entity, Location target): void -> 让实体看向指定位置
> controllerLookAt(LivingEntity entity, Entity target): void -> 让实体看向指定实体
> controllerJumpReady(LivingEntity entity): void -> 准备实体跳跃
> controllerJumpCurrent(LivingEntity entity): boolean -> 检查实体是否正在跳跃
> setFollowRange(LivingEntity entity, double value): void -> 设置实体的跟随范围

## 实现细节
- 作为抽象基类，定义了操作Minecraft实体AI的标准接口
- 有两个主要实现类：
  - PathfinderExecutorImpl: 适用于1.16及以下版本
  - PathfinderExecutorImpl17: 适用于1.17及以上版本
- 方法返回类型多为Object，实际上是对应版本的NMS对象

## 使用场景
> 在SimpleAiExecutor中通过nmsProxy动态选择合适的实现类
> 用于控制实体的AI行为，如移动、攻击、视线控制等
> 提供对实体AI系统的完整访问和操作能力

## 注意事项
> 类使用@SuppressWarnings("rawtypes")注解抑制泛型相关警告
> 返回类型多为Object，需要在实现类中进行适当的类型转换
> 实现类通过ASM生成，用于适配不同版本的Minecraft API
