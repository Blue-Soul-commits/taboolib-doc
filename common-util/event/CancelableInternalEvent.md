# CancelableInternalEvent
## 基本信息
- 类名和包路径: taboolib.common.event.CancelableInternalEvent
- 基本用途: 可取消的内部事件基类
- 类型: 抽象类(Abstract Class)
- 所属模块: TabooLib 公共模块
## 类结构
### 公开静态字段
> 无
### 公开静态方法
> 无
### 类内可被访问字段
> isCancelled: Boolean -> 表示事件是否被取消
### 类方法
> callIf(): Boolean -> 触发事件并返回事件是否未被取消
## 实现细节
> 继承自 InternalEvent
> 添加 isCancelled 属性用于标记事件是否被取消
> 提供 callIf() 方法，触发事件并返回事件是否未被取消
## 使用场景
> 创建需要支持取消功能的事件
> 在需要根据事件是否被取消来决定后续操作的场景
## 注意事项
> 监听器可以通过设置 isCancelled = true 来取消事件
> 可以使用 callIf() 方法在触发事件后检查事件是否被取消