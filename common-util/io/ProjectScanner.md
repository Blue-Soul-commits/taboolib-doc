# ProjectScanner

## 基本信息
- 类名和包路径: taboolib.common.io (工具类文件)
- 基本用途: 扫描和管理项目中的类和资源文件
- 类型: Kotlin工具类和扩展函数集合
- 所属模块: common-io

## 类结构
### 公开静态字段
> runningClassMapInJar: Map<String, ReflexClass> -> 当前插件JAR中的所有类
> runningClassMap: Map<String, ReflexClass> -> 当前插件的所有类(包括动态加载的)
> runningClassMapWithoutLibrary: Map<String, ReflexClass> -> 当前插件的所有类(排除第三方库)
> runningClasses: List<ReflexClass> -> 当前插件所有类的集合
> runningClassesWithoutLibrary: List<ReflexClass> -> 当前插件所有类的集合(排除第三方库)
> runningExactClassMap: Map<String, ReflexClass> -> 当前插件的所有类(排除匿名类和内部类)
> runningExactClasses: List<ReflexClass> -> 当前插件所有类的集合(排除匿名类和内部类)
> runningResourcesInJar: Map<String, ByteArray> -> 当前插件JAR中的所有资源文件
> runningResources: Map<String, ByteArray> -> 当前插件的所有资源文件(包括动态加载的)
> extraLoadedFiles: CopyOnWriteArrayList<File> -> 由ClassAppender加载的文件
> extraLoadedClasses: ConcurrentHashMap<String, ReflexClass> -> 由ClassAppender加载的类
> extraLoadedResources: ConcurrentHashMap<String, ByteArray> -> 由ClassAppender加载的资源文件

### 公开静态方法
> URL.getClasses(classLoader: ClassLoader): Map<String, ReflexClass> -> 获取URL下的所有类
> URL.getResources(): MutableMap<String, ByteArray> -> 获取URL下的所有资源文件

### 类内可被访问字段
> 无

### 类方法
> init() -> 初始化函数，注册ClassAppender回调

## 实现细节
- 使用懒加载模式初始化`runningClassMapInJar`和`runningResourcesInJar`
- 支持从系统属性`taboolib.scan`和`taboolib.main`中获取额外扫描入口
- 使用并行流处理JAR文件中的类和资源，提高扫描效率
- 利用BinaryCache缓存已解析的类信息，避免重复解析
- 通过ClassAppender回调机制动态收集加载的类和资源

## 使用场景
> 需要获取项目中所有类的信息时，如注解处理
> 需要访问项目中的资源文件时
> 需要区分项目自身类和第三方库类时
> 需要监控动态加载的类和资源时

## 注意事项
> 初始扫描可能较耗时，特别是对于大型项目
> 线程安全考虑：使用了ConcurrentHashMap和CopyOnWriteArrayList
> 资源文件会被完全加载到内存中，可能占用较多内存
