# ConfigLoader
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConfigLoader
- 基本用途: 自动加载和处理带有 @Config 注解的配置文件字段
- 类型: 类 (Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> files: HashMap<String, ConfigNodeFile> -> 存储已加载的配置文件，键为配置文件名

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> visit(field: ClassField, owner: ReflexClass) -> 处理带有 @Config 注解的字段
> getLifeCycle(): LifeCycle -> 返回类访问器的生命周期阶段

## 实现细节
- 继承自 ClassVisitor 类，优先级为 1
- 使用 @Inject 和 @Awake 注解，在 TabooLib 初始化时自动加载
- 通过 @RuntimeDependencies 声明运行时依赖，包括：
  - snakeyaml 2.2 (YAML 解析)
  - typesafe config 1.4.3 (HOCON 配置)
  - night-config 系列库 3.6.7 (配置文件处理)
- 在 INIT 生命周期阶段执行，处理所有带有 @Config 注解的字段
- 支持配置文件的自动重载功能，通过 FileWatcher 监听文件变更
- 支持 ConfigNode 注解的处理，在配置重载时重新绑定节点

## 使用场景
> 自动加载和绑定配置文件到类字段
> 实现配置文件的自动重载功能
> 在插件初始化阶段自动处理配置文件

## 注意事项
> 配置文件会从资源文件释放到插件数据文件夹
> 同名配置文件只会加载一次，后续使用缓存的实例
> 支持 SecuredFile 类型的特殊处理
> 自动重载功能会增加文件系统监听器的开销
