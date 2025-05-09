# KetherLoader

## 基本信息
- 类名和包路径: taboolib.module.kether.KetherLoader
- 基本用途: Kether脚本引擎的类加载器，自动发现和注册带有KetherParser和KetherProperty注解的方法
- 类型: 类和伴生对象
- 所属模块: kether

## 类结构
### 公开静态字段
> sharedParser: ArrayList<Pair<Array<String>, String>> -> 存储已注册的共享解析器信息
> sharedScriptProperty: ArrayList<Pair<String, String>> -> 存储已注册的共享属性信息

### 公开静态方法
> registerParser(parser: ScriptActionParser<*>, name: Array<String>, namespace: String = "kether", shared: Boolean = false): Unit -> 注册脚本动作解析器
> registerProperty(property: ScriptProperty<*>, bind: Class<*>, shared: Boolean = false): Unit -> 注册脚本属性处理器

### 类内可被访问字段
> 无

### 类方法
> visit(method: ClassMethod, owner: ReflexClass): Unit -> 实现ClassVisitor接口的方法，处理类方法的注解
> getLifeCycle(): LifeCycle -> 返回类加载生命周期阶段

## 实现细节
- KetherLoader继承自ClassVisitor，实现了TabooLib的类访问器机制
- 使用@Awake和@Inject注解标记为自动加载
- 在visit方法中检测并处理带有@KetherParser和@KetherProperty注解的方法
- 伴生对象使用@Inject注解标记，包含共享组件的管理功能
- 在插件禁用阶段(DISABLE)自动清理已注册的共享组件
- 通过StandardChannel实现跨插件的组件共享
- 支持静态方法和实例方法的注解处理

## 使用场景
> 自动发现和注册Kether脚本动作解析器
> 自动发现和注册Kether脚本属性处理器
> 实现跨插件的组件共享和管理
> 简化Kether脚本扩展的开发流程

## 注意事项
> 类加载发生在LOAD生命周期阶段，确保优先加载
> 共享组件会在插件禁用时自动注销，避免资源泄漏
> 使用TabooLib的Reflex库进行反射操作，提高兼容性
> 对TabooLib路径的类名进行特殊处理，使用"@"前缀简化
> 需要正确处理类实例的获取，支持静态方法和实例方法
