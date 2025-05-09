# ConfigNodeLoader
## 基本信息
- 类名和包路径: taboolib.module.configuration.ConfigNodeLoader
- 基本用途: 处理带有 @ConfigNode 注解的字段，将配置文件中的节点值绑定到字段
- 类型: 类 (Class)
- 所属模块: basic-configuration

## 类结构
### 公开静态字段
> 无

### 公开静态方法
> 无

### 类内可被访问字段
> 无

### 类方法
> visit(field: ClassField, owner: ReflexClass) -> 处理带有 @ConfigNode 注解的字段
> getLifeCycle(): LifeCycle -> 返回类访问器的生命周期阶段
> String.toNode(): String -> 扩展函数，将驼峰命名转换为连字符命名

## 实现细节
- 继承自 ClassVisitor 类，优先级为 2（比 ConfigLoader 的优先级低）
- 使用 @Inject 和 @Awake 注解，在 TabooLib 初始化时自动加载
- 在 INIT 生命周期阶段执行，处理所有带有 @ConfigNode 注解的字段
- 支持从类级别的 @ConfigNode 注解继承配置文件名称
- 自动为不包含扩展名的配置文件名添加 .yml 后缀
- 支持将字段名自动转换为配置节点路径（驼峰转连字符）
- 支持基本类型的自动转换（Integer, Character, Byte, Long, Double, Float, Short, Boolean）
- 支持 ConfigNodeTransfer 类型的特殊处理，用于复杂类型转换

## 使用场景
> 将配置文件中的特定节点值绑定到类字段
> 实现配置节点与代码的自动映射
> 在配置重载时自动更新绑定的字段值
> 处理复杂类型的配置值转换

## 注意事项
> 如果配置文件未定义或节点不存在，会输出警告信息
> 字段名会自动转换为配置节点路径，例如 "databaseHost" 会转换为 "database-host"
> 配置文件必须先通过 @Config 注解加载，才能被 @ConfigNode 引用
> 支持在类级别定义默认的配置文件名称

