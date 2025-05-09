# SimpleAi

## 基本信息
- 类名和包路径: taboolib.module.ai.SimpleAi
- 基本用途: 实体 AI 行为的抽象基类，用于定义实体的 AI 行为模式
- 类型: 抽象类
- 所属模块: bukkit-nms-ai

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> shouldExecute(): Boolean -> 判断 AI 是否应该开始执行
> continueExecute(): Boolean -> 判断 AI 是否应该继续执行，默认返回 shouldExecute() 的结果
> startTask(): Unit -> AI 开始执行时的操作
> resetTask(): Unit -> AI 重置时的操作
> updateTask(): Unit -> AI 更新时的操作

## 实现细节
- SimpleAi 是一个抽象类，需要被继承并实现其抽象方法
- 只有 shouldExecute() 方法是抽象的，必须由子类实现
- continueExecute() 方法默认调用 shouldExecute()，可以被子类重写以提供不同的逻辑
- startTask()、resetTask() 和 updateTask() 方法默认实现为空操作 (Unit)，可以被子类重写

## 使用场景
> 创建自定义实体 AI 行为，如寻路、攻击、逃跑等
> 替换或扩展原版 Minecraft 实体的 AI 行为

## 注意事项
> 实现类必须至少实现 shouldExecute() 方法
> 在高频率调用的方法中应避免复杂计算，以防止性能问题
