# PathfinderCreatorImpl17

## 基本信息
- 类名和包路径: taboolib.module.ai.PathfinderCreatorImpl17
- 基本用途: 为1.17及以上版本Minecraft提供PathfinderGoal实现的适配器类
- 类型: 具体实现类
- 所属模块: bukkit-nms-ai

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> simpleAI: SimpleAi -> 存储被适配的SimpleAi实例

### 类方法
> PathfinderCreatorImpl17() -> 无参构造函数
> PathfinderCreatorImpl17(SimpleAi ai) -> 带参构造函数，初始化simpleAI字段
> createPathfinderGoal(SimpleAi ai): Object -> 实现PathfinderCreator接口，创建新的PathfinderCreatorImpl17实例
> canUse(): boolean -> 重写PathfinderGoal方法，对应shouldExecute
> canContinueToUse(): boolean -> 重写PathfinderGoal方法，对应continueExecute
> start(): void -> 重写PathfinderGoal方法，对应startTask
> stop(): void -> 重写PathfinderGoal方法，对应resetTask
> tick(): void -> 重写PathfinderGoal方法，对应updateTask

## 实现细节
- 继承自net.minecraft.world.entity.ai.goal.PathfinderGoal，实现PathfinderCreator接口
- 作为适配器，将SimpleAi接口的方法映射到Mojang映射的PathfinderGoal方法
- 方法映射关系：
  - canUse() -> shouldExecute()
  - canContinueToUse() -> continueExecute()
  - start() -> startTask()
  - stop() -> resetTask()
  - tick() -> updateTask()

## 使用场景
> 在1.17及以上版本的Minecraft服务器中使用
> 通过nmsProxy动态选择，用于创建实体AI行为
> 特别适用于Paper服务端使用Mojang映射的环境

## 注意事项
> 类注释明确指出"该类仅用作生成 ASM 代码，无任何意义"
> 实际上该类是ASM生成的模板，会被AsmClassTranslation处理
> 与PathfinderCreatorImpl不同，此类使用Mojang映射的方法名(canUse, canContinueToUse等)
> 包路径也从net.minecraft.server变为net.minecraft.world.entity.ai.goal
