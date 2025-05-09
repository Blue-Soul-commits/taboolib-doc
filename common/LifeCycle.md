# LifeCycle

## 基本信息

- 类名和包路径: taboolib.common.LifeCycle
- 基本用途: 定义插件的生命周期阶段
- 类型: 枚举
- 所属模块: Common

---

## 类结构

### 公开静态字段

> NONE: LifeCycle -> 未启动状态
> 
> CONST: LifeCycle -> 插件初始化（静态代码块被执行时）阶段
> 
> INIT: LifeCycle -> 插件主类被实例化阶段
> 
> LOAD: LifeCycle -> 插件加载阶段
> 
> ENABLE: LifeCycle -> 插件启用阶段
> 
> ACTIVE: LifeCycle -> 服务器完全启动（调度器启动）阶段
> 
> DISABLE: LifeCycle -> 插件卸载阶段

### 公开静态方法

> (无静态方法)

### 类内可被访问字段

> (无额外字段)

### 类方法

> (无实例方法)

---

## 实现细节

- 定义了插件从加载到卸载的完整生命周期

- 提供了明确的生命周期顺序，按照枚举声明顺序排列

---

## 使用场景

> 在 TabooLib.registerLifeCycleTask 中指定任务执行的生命周期阶段  
> 判断当前插件所处的生命周期阶段

## 注意事项

> 生命周期是按照顺序执行的，当前生命周期之前的任务无法再执行
