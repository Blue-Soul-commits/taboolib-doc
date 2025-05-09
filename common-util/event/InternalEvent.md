# InternalEvent

## 基本信息
- 类名和包路径: taboolib.common.event.InternalEvent
- 基本用途: 内部事件系统的基类，提供事件触发功能
- 类型: 抽象类(Abstract Class)
- 所属模块: TabooLib 公共模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> call(): Unit -> 触发当前事件实例

## 实现细节
- 作为所有内部事件的基类
- 提供 call() 方法简化事件触发过程
- 内部调用 InternalEventBus.call(this) 实现事件分发

## 使用场景
> 创建自定义事件类型
> 在代码中触发事件

## 注意事项
> 所有自定义事件都应继承此类
> 可以直接在事件实例上调用 call() 方法触发事件
