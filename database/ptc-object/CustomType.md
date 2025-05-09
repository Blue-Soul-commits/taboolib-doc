# CustomType
## 基本信息 
- 类名和包路径: taboolib.expansion.CustomType 
- 基本用途: 为持久化框架提供自定义类型的序列化和反序列化支持
- 类型: 接口
- 所属模块: module/database/database-ptc-object

## 类结构 
### 属性
> val type: Class<*> -> 自定义类型的Java类
> val typeSQL: ColumnTypeSQL -> 对应的SQL数据库列类型，默认为TEXT
> val typeSQLite: ColumnTypeSQLite -> 对应的SQLite数据库列类型，默认为TEXT
> val length: Int -> 在数据库中的字段长度，默认为512

### 方法
> fun match(value: Any): Boolean -> 检查给定值是否匹配此自定义类型
> fun matchType(clazz: Class<*>): Boolean -> 检查给定类是否匹配此自定义类型
> fun serialize(value: Any): Any -> 将对象序列化为数据库可存储的格式
> fun deserialize(value: Any): Any -> 将数据库中的值反序列化为对象

## 实现细节
- CustomType接口定义了自定义类型的基本行为
- 默认实现使用TabooLib的Configuration工具进行JSON序列化和反序列化
- typeSQL和typeSQLite属性允许开发者为不同数据库引擎指定不同的列类型
- 序列化默认使用FAST_JSON格式将对象转换为字符串
- 反序列化过程使用ignoreConstructor=true参数，允许反序列化没有无参构造函数的类
- match和matchType方法用于类型匹配检查，在运行时判断对象或类是否适用于此自定义类型

## 使用场景 
> 持久化复杂对象到数据库
> 支持TabooLib ORM框架存储非基本类型
> 为自定义类型提供序列化和反序列化策略
> 在不修改现有类的情况下提供持久化能力

## 注意事项 
> 默认序列化使用FAST_JSON，确保对象的字段可以被正确序列化
> 默认列类型为TEXT，对于大对象可能需要调整length属性或使用更适合的列类型
> 反序列化时忽略构造函数，依赖于字段直接赋值
> 实现此接口的类需要注册到CustomTypeFactory才能生效

