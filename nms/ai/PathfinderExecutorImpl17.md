# PathfinderExecutorImpl17

## 基本信息
- 类名和包路径: taboolib.module.ai.PathfinderExecutorImpl17
- 基本用途: 为1.17及以上版本Minecraft提供实体AI行为控制的具体实现
- 类型: 具体实现类
- 所属模块: bukkit-nms-ai

## 类结构

### 私有字段
> pathEntity: Field? -> 存储PathEntity字段的反射引用
> pathfinderGoalSelectorSet: Field -> 存储PathfinderGoalSelector集合字段的反射引用
> controllerJumpCurrent: Field -> 存储ControllerJump当前状态字段的反射引用

### 初始化块
> 通过反射获取必要的字段引用，根据不同版本选择不同的字段名：
> - 对于PathfinderGoalSelector，根据版本选择"availableGoals"(UniversalCraftBukkit)、"c"(1.20.5+)或"d"
> - 对于ControllerJump，根据版本选择"jump"(UniversalCraftBukkit)或"a"
> 设置字段可访问性
> 查找NavigationAbstract中的PathEntity字段

### 方法实现
> getEntityInsentient(LivingEntity): Any -> 获取实体的NMS EntityInsentient对象
> getNavigation(LivingEntity): Any -> 获取实体的导航控制器
> getControllerJump(LivingEntity): Any -> 获取实体的跳跃控制器，根据版本返回不同实现
> getControllerMove(LivingEntity): Any -> 获取实体的移动控制器
> getControllerLook(LivingEntity): Any -> 获取实体的视线控制器，根据版本返回不同实现
> getGoalSelector(LivingEntity): Any -> 获取实体的目标选择器
> getTargetSelector(LivingEntity): Any -> 获取实体的目标选择器
> getPathEntity(LivingEntity): Any -> 通过反射获取实体的路径实体
> setPathEntity(LivingEntity, Any): void -> 通过反射设置实体的路径实体
> addGoalAi(LivingEntity, SimpleAi, Int): Unit -> 添加目标AI，使用pathfinderCreator创建PathfinderGoal
> addTargetAi(LivingEntity, SimpleAi, Int): Unit -> 添加目标选择AI，使用pathfinderCreator创建PathfinderGoal
> replaceGoalAi(LivingEntity, SimpleAi, Int): Unit -> 替换目标AI，调用重载方法
> replaceTargetAi(LivingEntity, SimpleAi, Int): Unit -> 替换目标选择AI，调用重载方法
> replaceGoalAi(LivingEntity, SimpleAi, Int, String?): Unit -> 根据名称或优先级替换目标AI
> replaceTargetAi(LivingEntity, SimpleAi, Int, String?): Unit -> 根据名称或优先级替换目标选择AI
> removeGoalAi(LivingEntity, Int): Unit -> 根据优先级移除目标AI
> removeTargetAi(LivingEntity, Int): Unit -> 根据优先级移除目标选择AI
> removeGoalAi(LivingEntity, String): Unit -> 根据名称移除目标AI
> removeTargetAi(LivingEntity, String): Unit -> 根据名称移除目标选择AI
> removeGoal(String, Any): Unit -> 私有方法，根据名称从选择器中移除目标
> removeGoal(Int, Any): Unit -> 私有方法，根据优先级从选择器中移除目标
> getGoal(Any): Collection<*> -> 私有方法，获取选择器中的目标集合
> clearGoalAi(LivingEntity): Unit -> 清除所有目标AI
> clearTargetAi(LivingEntity): Unit -> 清除所有目标选择AI
> getGoalAi(LivingEntity): Iterable<*>? -> 获取所有目标AI
> getTargetAi(LivingEntity): Iterable<*>? -> 获取所有目标选择AI
> setGoalAi(LivingEntity, Iterable<*>?): Unit -> 设置所有目标AI
> setTargetAi(LivingEntity, Iterable<*>?): Unit -> 设置所有目标选择AI
> navigationMove(LivingEntity, Location): Boolean -> 移动实体到指定位置，使用默认速度
> navigationMove(LivingEntity, Location, Double): Boolean -> 以指定速度移动实体到指定位置
> navigationMove(LivingEntity, LivingEntity): Boolean -> 移动实体到目标实体，使用默认速度
> navigationMove(LivingEntity, LivingEntity, Double): Boolean -> 以指定速度移动实体到目标实体
> navigationReach(LivingEntity): Boolean -> 检查实体是否到达目标位置
> controllerLookAt(LivingEntity, Location): Unit -> 让实体看向指定位置
> controllerLookAt(LivingEntity, Entity): Unit -> 让实体看向指定实体
> controllerJumpReady(LivingEntity): Unit -> 通过反射设置实体准备跳跃
> controllerJumpCurrent(LivingEntity): Boolean -> 通过反射检查实体是否正在跳跃
> setFollowRange(LivingEntity, Double): Unit -> 设置实体的跟随范围属性

## 实现细节
- 使用反射和UnsafeAccess访问和修改NMS类的私有字段
- 通过类型转换将Bukkit实体转换为NMS实体
- 处理不同Minecraft版本的API差异，特别是Paper 1.20.5+使用Mojang映射
- 支持通过名称或优先级管理实体的AI目标
- 与PathfinderExecutorImpl相比，使用了Mojang映射的方法名(如addGoal, moveTo, canReach等)

## 使用场景
> 在1.17及以上版本的Minecraft服务器中使用
> 通过nmsProxy动态选择，用于控制实体的AI行为
> 特别适用于Paper服务端使用Mojang映射的环境
> 提供对实体AI系统的完整访问和操作能力

## 注意事项
> 类注释明确指出"该类仅用作生成 ASM 代码，无任何意义"
> 实际上该类是ASM生成的模板，会被AsmClassTranslation处理
> 大量使用反射和类型转换，依赖于NMS内部结构
> 通过MinecraftVersion.isUniversalCraftBukkit和MinecraftVersion.majorLegacy判断不同版本
> 使用remap=true参数处理字段名映射问题

