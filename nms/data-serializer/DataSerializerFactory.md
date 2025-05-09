# DataSerializerFactory

## 基本信息
- 类名和包路径: taboolib.module.nms.DataSerializerFactory
- 基本用途: 提供创建 DataSerializer 实例的工厂接口
- 类型: 接口
- 所属模块: bukkit-nms-data-serializer

## 类结构

### 公开静态字段
> instance: DataSerializerFactory -> 根据 Minecraft 版本获取适当的工厂实例

### 公开静态方法
> 无

### 顶层函数
> createDataSerializer(builder: DataSerializer.() -> Unit = {}): DataSerializer -> 创建一个 DataSerializer 实例（旧名称）
> dataSerializerBuilder(builder: DataSerializer.() -> Unit = {}): DataSerializer -> 创建一个 DataSerializer 实例

### 抽象方法
> newSerializer(): DataSerializer -> 创建新的序列化器实例

## 实现细节
- 使用 unsafeLazy 延迟初始化单例实例
- 根据 Minecraft 版本选择不同的实现类：
  - 1.20.5+ 版本使用 DataSerializerFactory12005
  - 1.20.4 及以下版本使用 DataSerializerFactoryLegacy
- 使用 nmsProxy 创建代理实例，避免直接依赖特定版本的实现
- 提供两个顶层函数用于创建 DataSerializer 实例，支持 Kotlin DSL 风格的构建器模式

## 使用场景
> 创建适用于当前 Minecraft 版本的 DataSerializer 实例
> 序列化数据以便在网络上传输
> 创建自定义数据包

## 注意事项
> createDataSerializer 和 dataSerializerBuilder 函数功能相同，前者是为了兼容性保留
> 工厂实例会根据当前运行的 Minecraft 版本自动选择合适的实现

