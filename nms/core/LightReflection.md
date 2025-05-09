# LightReflection

## 基本信息
- 类名和包路径: taboolib.module.nms.LightReflection
- 基本用途: 处理 Paper 1.20.6+ 中的 Mojang Mapping 兼容性问题，为 TabooLib 提供类加载重映射支持
- 类型: 工具类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> PAPER_REFLECTION_HOLDER: String -> Paper 反射持有者类的完全限定名
> PAPER_REFLECTION_REMAPPER: String -> Paper 反射重映射器类的完全限定名

### 公开静态方法
> forName(name: String, initialize: boolean, loader: ClassLoader): Class<?> -> 使用 Paper 的重映射机制加载类

### 类内可被访问字段
> paperReflectionHolder: Class<?> -> Paper 反射持有者类的 Class 对象
> forName: Method -> Paper 反射持有者类中的 forName 方法

### 类方法
> init(): void -> 初始化并接管 TabooLib 的类查找器

## 实现细节
- 通过反射获取 Paper 的类重映射机制
- 在静态初始化块中尝试加载 Paper 的反射相关类和方法
- 提供自定义的 ClassFinder 实现，替换 TabooLib 默认的类查找机制
- 当 Paper 的反射机制不可用时（非 Paper 服务器或版本低于 1.20.6），回退到标准的 Class.forName 方法

## 使用场景
> 在 Paper 1.20.6+ 服务器上运行 TabooLib
> 处理 Mojang Mapping 与传统 Spigot 映射之间的兼容性
> 确保使用旧映射名称编写的代码在新版 Paper 上正常工作
> 为 TabooLib 的 NMS 访问提供透明的重映射支持

## 注意事项
> 仅在 Paper 1.20.6+ 服务器上有效
> 由 "extra.properties" 启动，不应手动调用 init() 方法
> 依赖于 Paper 的内部 API，可能会随着 Paper 的更新而需要调整
> 异常处理设计确保在不支持的环境中优雅降级

