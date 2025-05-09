# RemapReflex

## 基本信息
- 类名和包路径: taboolib.module.nms.remap.RemapReflex
- 基本用途: 提供反射重映射功能的抽象基类，用于处理Minecraft服务器环境中的字段和方法名称映射
- 类型: 抽象类
- 所属模块: bukkit-nms

## 类结构

### 公开静态字段
> 无公开静态字段

### 公开静态方法
> 无公开静态方法

### 类内可被访问字段
> isUniversal: Boolean -> 是否为通用版本环境
> major: Int -> Minecraft主版本号
> fieldRemapCacheMap: ConcurrentHashMap<String, String> -> 字段重映射缓存
> methodRemapCacheMap: ConcurrentHashMap<String, String> -> 方法重映射缓存
> descriptorTypeCacheMap: ConcurrentHashMap<String, List<Class<*>>> -> 描述符类型缓存
> spigotMapping: Mapping -> Spigot映射信息
> paperMapping: Mapping -> Paper映射信息

### 类方法
> saveField(namespace: String, old: String, new: String): Unit -> 保存字段映射信息到缓存
> saveMethod(namespace: String, old: String, new: String, descriptor: String?): Unit -> 保存方法映射信息到缓存

## 实现细节
- 继承自ReflexRemapper接口，提供反射重映射功能
- 使用Exchanges系统存储和获取缓存信息，确保跨类加载器共享
- 在开发者模式下，会将映射信息保存到.dev/remap.txt文件中，便于调试
- 初始化时会清除之前的映射记录文件

## 使用场景
> 在Bukkit/Spigot/Paper服务器环境中处理NMS类的反射访问
> 为不同Minecraft版本提供统一的反射API，处理混淆名称差异

## 注意事项
> 这是一个抽象类，需要通过子类实现具体的field和method方法
> 子类实现包括RemapReflexSpigot和RemapReflexPaper，分别用于不同服务器环境

