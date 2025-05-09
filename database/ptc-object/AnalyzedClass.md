# AnalyzedClass
## 基本信息 
- 类名和包路径: taboolib.expansion.AnalyzedClass 
- 基本用途: 解析并分析数据类结构，支持ORM框架实现类与表的映射
- 类型: 类
- 所属模块: module/database/database-ptc-object

## 类结构 
### 构造函数
> private constructor(val clazz: Class<*>) -> 私有构造函数，通过of静态方法访问

### 属性
> val clazz: Class<*> -> 被分析的类
> private val primaryConstructor -> 主构造器
> private val memberProperties -> 类字段映射
> val members: List<AnalyzedClassMember> -> 解析后的成员列表
> val primaryMember: AnalyzedClassMember? -> 被@Id标记的主键成员
> val primaryMemberName: String? -> 主键成员名称
> val wrapperObjectInstance: Any? -> 伴生对象实例（如果存在）
> val wrapperFunction: Method? -> 自定义反序列化方法（接收BundleMap参数）

### 方法
> fun getPrimaryMemberValue(data: Any): Any -> 获取对象的主键值
> fun getValue(data: Any, member: AnalyzedClassMember): Any -> 获取对象指定成员的值
> fun read(result: ResultSet): Map<String, Any?> -> 从数据库结果集读取数据映射
> fun <T> createInstance(map: Map<String, Any?>): T -> 从数据映射创建类实例
> fun validation(parameter: Parameter): Parameter -> 验证参数合法性

### 伴生对象
> val cached: ConcurrentHashMap<Class<*>, AnalyzedClass> -> 类分析结果缓存
> fun of(clazz: Class<*>): AnalyzedClass -> 创建或获取类分析实例

## 实现细节
- 使用私有构造函数和缓存机制提高性能
- 通过反射检查类的构造器、字段和注解信息
- 将每个构造器参数与对应字段关联并创建AnalyzedClassMember
- 自动检测@Id注解标记的主键成员，并验证唯一性
- 自动检测伴生对象中的自定义反序列化方法
- 支持自定义类型的序列化和反序列化，通过CustomTypeFactory查找处理器
- 自动设置字段可访问性，避免私有字段访问限制
- 在初始化时验证自定义类型的可用性和主键的唯一性
- 支持从ResultSet读取数据并转换为适当类型
- 通过两种方式创建实例：自定义反序列化方法或构造函数调用

## 使用场景 
> ORM框架中解析数据类结构
> 数据库结果到对象的映射和转换
> 对象到数据库记录的序列化
> 支持自定义反序列化逻辑

## 注意事项 
> 每个数据类必须有一个主构造器
> 最多只能有一个成员被@Id标记为主键
> 不支持可变参数
> 自定义类型必须通过CustomTypeFactory注册
> 所有字段将被设置为可访问，即使是private
> 使用的类必须是规范的数据类，字段类型与构造器参数对应

