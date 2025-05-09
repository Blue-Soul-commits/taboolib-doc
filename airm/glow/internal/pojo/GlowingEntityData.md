# GlowingEntityData

## 基本信息
- 类名和包路径: top.maplex.arim.tools.glow.internal.pojo.GlowingEntityData
- 基本用途: 存储实体发光效果的相关数据
- 类型: 数据类(class)
- 所属模块: 发光效果工具模块 - 内部数据结构

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> teamID: String -> 实体所属的团队ID，用于控制发光颜色
> color: NamedTextColor -> 发光效果的颜色，可变属性
> otherSharedFlags: Byte -> 实体的其他共享标志位

### 类方法
> 无额外的类方法

## 实现细节
- 作为数据传输对象(DTO)，主要用于存储实体发光效果的相关数据
- 使用Adventure API的NamedTextColor表示发光颜色
- 字段color被声明为var，表示可以在创建对象后修改发光颜色
- 存储了团队ID，这是实现彩色发光效果的关键，Minecraft通过团队系统控制发光颜色
- otherSharedFlags保存了实体原本的共享标志位，以便在取消发光时恢复
- 不包含业务逻辑，纯粹作为数据载体使用

## 使用场景
> 在内部发光管理系统中跟踪和管理正在发光的实体
> 当需要修改已存在的实体发光效果颜色时，存储必要的引用数据
> 在移除发光效果时，用于恢复实体原本的标志位状态
> 在多玩家环境中，为不同玩家维护各自可见的实体发光效果

## 注意事项
> 这是内部类(internal.pojo)，主要供发光系统内部使用
> teamID对应Minecraft记分板系统中的团队ID，用于控制发光颜色
> 每个发光实体(对单个观察者可见)对应一个GlowingEntityData实例
> 修改color字段可以实时更新实体的发光颜色，而不需要重新创建发光效果
> otherSharedFlags保存了除发光标志位外的其他标志位，确保不会干扰实体的其他状态
