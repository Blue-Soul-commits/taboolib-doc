# RemapTranslationLegacy

## 基本信息
- 类名和包路径: taboolib.module.nms.remap.RemapTranslationLegacy
- 基本用途: 提供旧版本Minecraft环境下的字节码重映射功能，处理字段和方法名的转换
- 类型: 开放类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> parentsCacheMap: ConcurrentHashMap<String, List<String>> -> 缓存类的父类和接口信息

### 类方法
> mapFieldName(owner: String, name: String, descriptor: String): String -> 重写Remapper的mapFieldName方法，处理字段名映射
> mapMethodName(owner: String, name: String, descriptor: String): String -> 重写Remapper的mapMethodName方法，处理方法名映射

## 实现细节
- 继承自RemapTranslation类，专门处理旧版本Minecraft环境下的映射
- 字段映射过程：
  1. 仅在通用版本(isUniversal为true，即1.17+)中进行处理
  2. 获取运行时的类名并转换格式
  3. 使用parentsCacheMap缓存类的继承关系，避免重复查找
  4. 在Spigot映射中查找字段的Mojang混淆名
- 方法映射过程：
  1. 仅在major >= 10 (即1.18+)中进行处理
  2. 使用SignatureWriter和SignatureReader处理方法描述符中的类型引用
  3. 获取运行时的类名并转换格式
  4. 使用parentsCacheMap缓存类的继承关系
  5. 在Spigot映射中查找方法的Mojang混淆名，同时考虑方法参数类型

## 使用场景
> 在旧版本Minecraft环境中用于转译NMS类
> 在AsmClassTranslation中作为非Universal环境下的默认转换器

## 注意事项
> 字段映射仅在Minecraft 1.17+版本中启用
> 方法映射仅在Minecraft 1.18+版本中启用
> 使用parentsCacheMap缓存继承关系，提高性能
> 方法描述符中的类型引用也需要进行转换

