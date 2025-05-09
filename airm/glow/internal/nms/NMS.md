# NMS

## 基本信息
- 类名和包路径: top.maplex.arim.tools.glow.internal.nms.NMS
- 基本用途: 提供与Minecraft原生服务器(NMS)交互的抽象接口，用于发光效果实现
- 类型: 抽象类(abstract class)
- 所属模块: 发光效果工具模块 - 内部NMS实现

## 类结构

### 公开静态字段
> INSTANCE: NMS -> 通过taboolib的nmsProxy懒加载获取NMS实现实例

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> entitySharedFlagsID: Any? -> 获取实体DataWatcher标志位Flags的ID抽象属性

### 类方法
> getEntityFlags(entity: Entity): Byte? -> 获取NMS实体DataWatcher的标志位Flags
> getCombinedID(location: Location): Int? -> 获取指定位置方块的CombinedID

## 实现细节
- 使用TabooLib的nmsProxy系统实现不同Minecraft版本的兼容性
- 采用抽象类设计，定义接口规范，由具体版本的实现类提供实现
- 使用unsafeLazy进行实例的懒加载初始化，避免启动时就加载NMS相关代码
- 提供访问实体数据观察器(DataWatcher)和方块ID的方法，用于发光效果的实现

## 使用场景
> 在发光效果系统内部使用，为IGlow API提供底层支持
> 处理实体发光时需要修改实体的DataWatcher标志位
> 处理方块发光时需要获取方块的CombinedID
> 作为跨版本兼容层，隔离具体版本的NMS实现细节

## 注意事项
> 这是内部类(internal)，不应直接被外部模块使用
> 返回值类型为可空类型(Byte?和Int?)，调用时需要处理null情况
> 具体实现依赖于TabooLib的nmsProxy系统，需要为每个支持的Minecraft版本提供对应实现