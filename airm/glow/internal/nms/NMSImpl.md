# NMSImpl

## 基本信息
- 类名和包路径: top.maplex.arim.tools.glow.internal.nms.NMSImpl
- 基本用途: NMS抽象类的具体实现，提供跨版本的Minecraft原生服务器(NMS)交互实现
- 类型: 具体类(继承自NMS抽象类)
- 所属模块: 发光效果工具模块 - 内部NMS实现

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> nmsLegacyEntityInst: Class<NMSLegacyEntity> -> 旧版本NMS实体类
> nmsUniversalEntityInst: Class<NMSUniversalEntity> -> 通用版本NMS实体类
> nmsLegacyBlockInst: Class<NMSLegacyBlock> -> 旧版本NMS方块类
> nmsUniversalBlockInst: Class<NMSUniversalBlock> -> 通用版本NMS方块类
> entitySharedFlagsID: Any? -> 实现NMS抽象类的实体共享标志ID属性

### 类方法
> getEntityFlags(entity: Entity): Byte? -> 获取实体的DataWatcher标志位Flags
> getCombinedID(location: Location): Int? -> 获取指定位置方块的CombinedID

## 实现细节
- 使用类型别名(typealias)简化不同版本NMS类的引用
- 根据Minecraft版本ID(versionId)使用不同的实现路径
- 将Minecraft版本分为两大类：旧版本(Legacy)和通用版本(Universal，指1.17及以上)
- 使用反射技术(taboolib.library.reflex)访问NMS类的属性和方法
- 详细处理了1.12.2(11202)和1.16.5(11604)两个Legacy版本的特殊情况
- 对于不支持的版本，会输出警告日志并返回null
- 使用懒加载方式初始化entitySharedFlagsID属性，减少启动时的资源消耗

## 使用场景
> 在发光效果系统内部使用，为IGlow API提供底层支持
> 跨Minecraft版本实现实体和方块的发光效果
> 处理不同版本的NMS API差异，提供统一的接口

## 注意事项
> 目前完全支持的Minecraft版本有：1.12.2、1.16.5和通用版本(1.17+)
> 其他版本可能不受支持，会输出警告日志
> 使用了大量反射操作，可能在某些环境下存在性能开销
> 依赖于特定版本的CraftBukkit实现细节，服务端更新可能导致不兼容
> 这是内部类(internal)，不应直接被外部模块使用
