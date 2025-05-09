# Mapping

## 基本信息
- 类名和包路径: taboolib.module.nms.Mapping
- 基本用途: 提供 Minecraft 混淆映射表的加载和管理功能
- 类型: 数据类
- 所属模块: bukkit-nms

## 类结构

### 主要字段
> classMapSpigotS2F: MutableMap<String, String> -> Spigot 简单类名到完整类名的映射
> classMapSpigotToMojang: MutableMap<String, String> -> Spigot 完整类名到 Mojang 完整类名的映射
> classMapMojangToSpigot: MutableMap<String, String> -> Mojang 完整类名到 Spigot 完整类名的映射
> fields: MutableList<Field> -> 字段映射列表
> methods: MutableList<Method> -> 方法映射列表（1.18+）

### 内部类
> Field -> 字段映射数据类
  - path: String -> 类路径
  - mojangName: String -> Mojang 名称
  - translateName: String -> 转译名称
  - className: String -> 类名（从 path 中提取）

> Method -> 方法映射数据类（1.18+）
  - path: String -> 类路径
  - mojangName: String -> Mojang 名称
  - translateName: String -> 转译名称
  - descriptor: String -> 方法描述符
  - className: String -> 类名（从 path 中提取）

### 公开方法
> exchange(id: String): Mapping -> 将数据写入 Exchanges 空间并返回自身

### 伴生对象方法
> spigot(inputStreamCombined: InputStream, inputStreamFields: InputStream): Mapping -> 读取 Spigot 格式的映射文件
> paper(): Mapping -> 读取 Paper 格式 (reobf.tiny) 的映射文件
> exchange(id: String): Mapping -> 从 Exchanges 空间中读取数据

## SpigotMapping 类

### 主要字段
> combined: String -> 组合映射文件的哈希值
> fields: String -> 字段映射文件的哈希值

### 伴生对象
> OSS_URL: String -> 资源文件的基础 URL
> current: SpigotMapping? -> 当前运行环境所对应的 Spigot Mapping 文件

## 实现细节
- 使用 HashMap 和 LinkedList 存储映射数据，优化内存和性能
- 支持从 Spigot 和 Paper 格式的映射文件中加载数据
- 通过 Exchanges 机制在插件间共享映射数据，避免重复加载
- 自动下载当前 Minecraft 版本对应的映射文件
- 处理不同版本 Minecraft 的混淆差异（如 1.18+ 的方法映射）

## 映射文件格式说明
1. Spigot 格式:
   - 类映射: 从 combined 文件中读取，格式为 "类名 完整路径"
   - 字段映射: 从 fields 文件中读取，格式为 "类路径 Mojang名称 转译名称"
   - 方法映射: 从 fields 文件中读取，格式为 "类路径 Mojang名称 (参数描述符) 转译名称"

2. Paper 格式 (reobf.tiny):
   - 第一行为头信息，忽略
   - 类映射: 以 "c" 开头，格式为 "c Mojang路径 Spigot路径"
   - 方法映射: 以 "m" 开头，格式为 "m 描述符 Mojang解混淆名 Mojang混淆名"
   - 字段映射: 以 "f" 开头，格式为 "f 描述符 Mojang解混淆名 Mojang混淆名"

## 使用场景
> 在跨版本 Minecraft 开发中处理混淆名称
> 实现 NMS 代理功能，使代码在不同版本的 Minecraft 上兼容运行
> 在运行时将 Spigot 名称转换为 Mojang 名称，或反向转换
> 支持插件在 Paper 和 Spigot 服务器上的兼容性

## 注意事项
> 映射文件会在插件初始化时自动下载和加载
> 映射数据会通过 Exchanges 机制在插件间共享，减少内存占用
> 1.18+ 版本开始支持方法映射
> Paper 服务器在运行时使用 Mojang 解混淆名，而 Spigot 使用混淆名
