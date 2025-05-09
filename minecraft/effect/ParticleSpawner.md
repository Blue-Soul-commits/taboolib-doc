# ParticleSpawner

## 基本信息
- 类名和包路径: taboolib.module.effect.ParticleSpawner
- 基本用途: 定义粒子生成器的基本接口
- 类型: 接口(Interface)
- 所属模块: taboolib.module.effect

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> 无类内可被访问字段

### 类方法
> spawn(location: Location): Unit -> 在指定位置生成粒子

## 实现细节
- 这是一个简单的接口，只包含一个spawn方法
- spawn方法接收一个Location参数，表示要生成粒子的位置
- 返回类型为Unit（Kotlin中的void）
- 使用Kotlin语言编写，但可以在Java中正常使用

## 使用场景
> 作为粒子生成系统的基础接口
> 实现各种自定义粒子效果生成器
> 在粒子效果框架中作为标准接口使用
> 用于创建可复用的粒子效果组件

## 注意事项
> 接口只定义了生成粒子的方法，具体的粒子类型、数量等参数需要在实现类中定义
> 该接口由Sky创建于2021/6/30
> 作为一个基础接口，它很简洁，只专注于粒子生成的核心功能
> 使用了taboolib.common.util.Location作为位置参数，而不是Bukkit的Location
