# SerializationManager

## 基本信息
- 类名和包路径: taboolib.expansion.ioc.serialization.SerializationManager
- 基本用途: 管理IOC容器中的序列化和反序列化功能
- 类型: object (单例)
- 所属模块: database-ioc

## 类结构

### 公开静态字段
> function: ConcurrentHashMap<String, SerializeFunction> -> 存储注册的序列化函数

### 公开静态方法
> getFunction(data: Class<*>): SerializeFunction -> 获取适用于指定类的序列化函数
> serialize(data: Any): String -> 将对象序列化为字符串
> deserialize(data: Any, target: Class<*>, type: Type): Any? -> 将数据反序列化为指定类型的对象

## 实现细节
- 使用ConcurrentHashMap存储序列化函数，确保线程安全
- 通过@Component注解的function属性确定使用哪种序列化方式
- 当找不到指定的序列化函数时，触发SerializationGetFunctionEvent事件
- 默认使用"Gson"作为序列化函数

## 使用场景
> 序列化数据对象以便持久化存储
> 从存储中反序列化数据对象
> 为不同类型的数据选择不同的序列化策略

## 注意事项
> 使用前需确保至少注册了"Gson"序列化函数
> 序列化函数应在LifeCycle.CONST阶段注册
> 支持通过事件动态选择序列化函数
