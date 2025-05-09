# PathfinderCreator

## 基本信息
- 类名和包路径: taboolib.module.ai.PathfinderCreator
- 基本用途: 创建Minecraft实体AI寻路目标的工厂接口
- 类型: 接口
- 所属模块: bukkit-nms-ai

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 接口方法
> createPathfinderGoal(SimpleAi ai): Object -> 根据SimpleAi实例创建对应的寻路目标对象

## 实现细节
- 作为工厂接口，负责创建不同版本Minecraft的寻路目标实现
- 有两个主要实现类：
  - PathfinderCreatorImpl: 适用于1.16及以下版本
  - PathfinderCreatorImpl17: 适用于1.17及以上版本

## 使用场景
> 在SimpleAiExecutor中通过nmsProxy动态选择合适的实现类
> 用于创建实体AI行为，如移动、攻击、逃跑等寻路行为

## 注意事项
> 返回类型为Object，实际上是对应版本的PathfinderGoal实例
> 实现类通过ASM生成，用于适配不同版本的Minecraft API

