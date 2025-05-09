# InternalListener

## 基本信息
- 类名和包路径: taboolib.common.event.InternalListener
- 基本用途: 提供事件监听器的取消接口
- 类型: 接口(Interface)
- 所属模块: TabooLib 公共模块

## 类结构

### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> cancel(): Unit -> 取消事件监听

## 实现细节
- 简单接口设计，只包含一个取消方法
- 由 InternalEventBus 在注册监听器时返回实例
- 实现类通常是 InternalEventBus 的内部类

## 使用场景
> 当需要动态取消事件监听时使用
> 在插件生命周期结束时清理事件监听器

## 注意事项
> 调用 cancel() 方法后，相应的监听器将不再接收事件
> 应保存监听器注册时返回的 InternalListener 实例，以便后续取消
