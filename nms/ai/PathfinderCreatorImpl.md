# PathfinderCreatorImpl

## 基本信息
- 类名和包路径: taboolib.module.ai.PathfinderCreatorImpl
- 基本用途: 为1.16及以下版本Minecraft提供PathfinderGoal实现的适配器类
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
> PathfinderCreatorImpl() -> 无参构造函数
> PathfinderCreatorImpl(SimpleAi ai) -> 带参构造函数，初始化simpleAI字段
> createPathfinderGoal(SimpleAi ai): Object -> 实现PathfinderCreator接口，创建新的PathfinderCreatorImpl实例
> a(): boolean -> 重写PathfinderGoal方法，对应shouldExecute
> b(): boolean -> 重写PathfinderGoal方法，对应continueExecute
> c(): void -> 重写PathfinderGoal方法，对应startTask
> d(): void -> 重写PathfinderGoal方法，对应resetTask
> e(): void -> 重写PathfinderGoal方法，对应updateTask

## 实现细节
- 继承自net.minecraft.server.v1_16_R3.PathfinderGoal，实现PathfinderCreator接口
- 作为适配器，将SimpleAi接口的方法映射到NMS的PathfinderGoal方法
- 方法映射关系：
  - a() -> shouldExecute()
  - b() -> continueExecute()
  - c() -> startTask()
  - d() -> resetTask()
  - e() -> updateTask()

## 使用场景
> 在1.16及以下版本的Minecraft服务器中使用
> 通过nmsProxy动态选择，用于创建实体AI行为

## 注意事项
> 类注释明确指出"该类仅用作生成 ASM 代码，无任何意义"
> 实际上该类是ASM生成的模板，会被AsmClassTranslation处理
> 方法名(a,b,c,d,e)是NMS混淆后的方法名，对应不同版本可能会变化

