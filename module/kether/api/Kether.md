# Kether

## 基本信息
- 类名和包路径: taboolib.module.kether.Kether
- 基本用途: Kether脚本引擎的核心单例对象，负责初始化、管理脚本动作、属性和操作符
- 类型: 单例对象(object)
- 所属模块: kether

## 类结构
### 公开静态字段
> isAllowToleranceParser: Boolean -> 控制是否启用宽容解析器模式，默认为true
> scriptService: ScriptService -> 懒加载的脚本服务实例
> scriptRegistry -> 懒加载的脚本注册表实例
> registeredScriptProperty: HashMap<Class<*>, MutableMap<String, ScriptProperty<*>>> -> 存储已注册的脚本属性
> registeredPlayerOperator: LinkedHashMap<String, PlayerOperator> -> 存储已注册的玩家操作符

### 公开静态方法
> init() -> 初始化Kether引擎，注册文本转换器

### 类内可被访问字段
> 无

### 类方法
> addAction(name: Array<String>, parser: QuestActionParser): Unit -> 批量注册脚本动作解析器
> addAction(name: String, parser: QuestActionParser, namespace: String? = null): Unit -> 注册单个脚本动作解析器
> removeAction(name: String, namespace: String? = null): Unit -> 移除已注册的脚本动作解析器
> addPlayerOperator(name: String, operator: PlayerOperator): Unit -> 注册玩家操作符
> addScriptProperty(clazz: Class<*>, property: ScriptProperty<*>): Unit -> 注册脚本属性
> removeScriptProperty(clazz: Class<*>, id: String): Unit -> 移除已注册的脚本属性

## 实现细节
- Kether是一个单例对象，使用@Inject注解标记为自动注入
- 使用@RuntimeDependencies声明运行时依赖，包括Apache JEXL和MojangDataFixerUpper
- 在初始化时(INIT生命周期)注册KetherTransfer到Language.textTransfer
- 提供脚本动作、属性和玩家操作符的注册和管理功能
- 懒加载scriptService和scriptRegistry，确保在首次使用时才初始化
- 在脚本注册表初始化时注册基础动作，如noop和literal

## 使用场景
> 作为Kether脚本引擎的全局入口点和管理中心
> 注册和管理自定义的脚本动作、属性和玩家操作符
> 获取脚本服务和注册表实例
> 控制脚本解析器的行为，如宽容模式的开关

## 注意事项
> 脚本动作注册可以指定命名空间，默认为"kether"
> isAllowToleranceParser控制脚本解析的严格程度，启用时可以省略literal关键字
> 运行时依赖使用特殊的重定位和测试规则，确保兼容性
> 内部方法(internal)主要由注解处理器和框架内部使用，不应直接调用
