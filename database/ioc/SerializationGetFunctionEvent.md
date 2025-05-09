# SerializationGetFunctionEvent

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.event.SerializationGetFunctionEvent
- 基本用途: 获取序列化函数时触发的事件，允许动态修改使用的序列化方式
- 类型: class
- 所属模块: database-ioc

## 类结构

### 类内可被访问字段
> data: Any -> 需要序列化/反序列化的数据对象或类
> targetFlag: String -> 目标序列化函数的标识名称
> function: SerializeFunction -> 当前选择的序列化函数，可被修改

## 实现细节
- 继承自InternalEvent，提供事件触发机制
- 在SerializationManager.getFunction方法中被触发
- 允许在事件处理过程中修改使用的序列化函数

## 使用场景
> 为特定数据类型动态选择序列化方式
> 根据运行时条件调整序列化策略
> 监控和干预序列化过程

## 注意事项
> 事件不可取消，但可以修改function字段来更改序列化方式
> 在没有找到指定targetFlag的序列化函数时会触发此事件
> 默认会使用"Gson"作为fallback序列化函数