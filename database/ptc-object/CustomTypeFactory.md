# CustomTypeFactory
## 基本信息 
- 类名和包路径: taboolib.expansion.CustomTypeFactory 
- 基本用途: 自定义类型的注册和管理工厂，负责扫描、加载和提供CustomType实现
- 类型: 类（ClassVisitor的子类）
- 所属模块: module/database/database-ptc-object

## 类结构 
### 注解
> @Inject -> TabooLib注入注解，使类被TabooLib容器管理
> @Awake -> TabooLib生命周期注解，指示初始化时执行

### 方法
> override fun getLifeCycle(): LifeCycle -> 获取生命周期阶段，返回LifeCycle.INIT
> override fun visitStart(clazz: ReflexClass) -> 访问类的回调方法，用于自动注册CustomType实现

### 伴生对象属性
> val registeredTypes: ConcurrentHashMap<Class<*>, CustomType> -> 存储已注册的自定义类型

### 伴生对象方法
> fun getCustomType(value: Any): CustomType? -> 通过对象实例获取匹配的自定义类型处理器
> fun getCustomTypeByClass(clazz: Class<*>): CustomType? -> 通过类对象获取匹配的自定义类型处理器

## 实现细节
- 使用TabooLib的类扫描机制，自动发现和注册实现了CustomType接口的类
- 在生命周期INIT阶段执行，确保自定义类型在框架使用前已注册
- visitStart方法检查类是否实现了CustomType接口，如果是则通过反射创建实例并注册
- 使用ConcurrentHashMap存储类型映射，支持并发访问
- 提供两种查找方式：基于对象实例的match()和基于类对象的matchType()

## 使用场景 
> 自动扫描并注册CustomType实现
> 在序列化/反序列化过程中查找合适的类型处理器
> 为ORM框架提供自定义类型的支持
> 扩展框架支持新的复杂数据类型

## 注意事项 
> CustomType实现类必须有一个可访问的实例（通常是单例或具有无参构造函数）
> 实现CustomType接口的类会被自动注册，无需手动调用
> 使用@Inject和@Awake注解确保在框架初始化时被发现和加载
> 如需手动注册，可直接操作registeredTypes集合

